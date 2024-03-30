<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Block type</label>
      <select id="type" v-model="value">
        <option value="title">Heading</option>
        <option value="subtitle">Subtitle</option>
        <option value="text">Text</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Value</label>
      <textarea id="value" rows="3" v-model="textareaText"></textarea>
    </div>

    <button class="btn primary" :disabled="textareaText.length <= 3" @click.prevent="buildingTextarea">Get the result</button>
  </form>
</template>

<script>
  export default {
    emits: ['building'],
    data() {
      return {
        value: 'title',
        textareaText: '',
      }
    },
    methods: {
      buildingTextarea() {
        this.$emit('building', this.value, this.textareaText)
        this.textareaText = ''
        this.value = 'title'
      }
    }
  }  
</script>