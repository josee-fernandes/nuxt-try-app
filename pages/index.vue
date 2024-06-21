
<script setup lang="ts">
  const count = ref(1)
</script>

<template>
  <button @click="count++" class="btn">count: {{ count }}</button>
</template>
