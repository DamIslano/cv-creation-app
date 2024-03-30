<template>
  <p v-if="tag[0] === 'text'">
    {{tag[1]}}
  </p>
</template>

<script>
  export default {
    props: ['tag']
  }
</script>