
<script setup lang="ts">
  const count = ref(1)

  // custom object
  const handleToDoNavigation = () => navigateTo({
    path: '/todo',
  })
</script>

<template>
  <div className="flex flex-col gap-2 w-max">
    <button @click="count++" class="btn">count: {{ count }}</button>
  
    <NuxtLink to="/todo" class="link">ToDo Page | Link component</NuxtLink>
    <button @click="handleToDoNavigation" class="link">ToDo Page | Programmatic Navigation</button>
  </div>
</template>
