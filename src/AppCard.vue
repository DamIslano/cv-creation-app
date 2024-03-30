<template>
  <app-title :tag="tag"></app-title>
  <app-subtitle :tag="tag"></app-subtitle>
  <app-text :tag="tag"></app-text>
</template>

<script>
  import AppTitle from './AppTitle.vue';
  import AppSubtitle from './AppSubtitle.vue';
  import AppText from './AppText.vue';
  export default{
    props: ['tags', 'results'],
    data() {
      return {
        tag: this.tags
      }
    },
    components: {
      AppTitle,
      AppSubtitle,
      AppText
    }
  }
</script>