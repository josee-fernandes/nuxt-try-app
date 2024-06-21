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

  // raw url
  const handleCounterNavigation = () => navigateTo('/')
</script>

<template>
  <div class="flex flex-col gap-4 w-max">
    <div class="flex flex-col gap-2">
      <h1 class="title">Create todo</h1>
      <button v-on:click="createTodo()" class="btn">Create</button>
      <hr />
    </div>
    <div class="flex flex-col gap-2">
      <h1 class="title">Todos</h1>
      <ul>
        <li v-for="todo in todos" :key="todo.id" :style="todo.isChecked ? 'text-decoration: line-through' : ''">
          {{ todo.title }}
    
          <input type="checkbox" name="" id="" v-bind:checked="todo.isChecked" @change="toggleChecked(todo.id)" />
        </li>
      </ul>
      <hr />
    </div>
    <div class="flex flex-col gap-2">
      <NuxtLink to="/" class="link">Counter Page | Link component</NuxtLink>
      <button @click="handleCounterNavigation" class="link">Counter Page | Programmatic Navigation</button>
    </div>
  </div>
</template>