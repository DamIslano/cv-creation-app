<template>
  <h1 v-if="tag[0] === 'title'">
    {{tag[1]}}
  </h1>
</template>

<script>
  export default {
    props: ['tag']
  }
</script>