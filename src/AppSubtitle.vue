<template>
  <h2 v-if="tag[0] === 'subtitle'">
    {{tag[1]}}
  </h2>
</template>

<script>
  export default {
    props: ['tag']
  }
</script>