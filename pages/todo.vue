<script setup lang="ts">
  interface Todo {
    id: number
    title: string
    isChecked: boolean
  }

  const todos = ref<Todo[]>([])

  const createTodo = () => {

    const newId = todos.value.length ? todos.value[todos.value.length - 1].id + 1 : 0

    const newTodo: Todo = {
      id: newId,
      title: `New todo - ${newId}`,
      isChecked: false
    }

    todos.value.push(newTodo)
  }

  const toggleChecked = (id: number) => {
    const _todos = todos.value

    const newTodos = _todos.map(todo => todo.id === id ? { ...todo, isChecked: !todo.isChecked } : todo)

    todos.value = newTodos
  }
</script>

<template>
  <div class="flex flex-col gap-2 w-max">
    <h1 class="title">Create todo</h1>
    <button v-on:click="createTodo()" class="btn">Create</button>
    <h1 class="title">Todos</h1>
    <ul>
      <li v-for="todo in todos" :key="todo.id" :style="todo.isChecked ? 'text-decoration: line-through' : ''">
        {{ todo.title }}
  
        <input type="checkbox" name="" id="" v-bind:checked="todo.isChecked" @change="toggleChecked(todo.id)" />
      </li>
    </ul>
  </div>
</template>