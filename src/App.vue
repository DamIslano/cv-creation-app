<template>
  <div class="container column">
    <app-form
      @building="constructing"
    ></app-form>
    <div class="card card-w70">
      <app-card :tags="tags" :results="results" v-for="result in results" :key="result"></app-card>
      <h3 v-if="this.results.length === 0">Choose the type of the block</h3>
    </div>
  </div>
  <div class="container">
    <p>
      <button class="btn primary" @click="loadComments">Load comments</button>
    </p>
    <div class="card" v-if="isLoaded">
      <h2>Comments</h2>
      <ul class="list" v-for="person in people" :key="person.id">
        <li class="list-item">
          <div>
            <p><strong>{{person.email}}</strong></p>
            <small>{{person.name}}</small>
          </div>
        </li>
      </ul>
    </div>
    <app-loader v-if="loading"></app-loader>
  </div>
</template>

<script>
import axios from 'axios';
import AppLoader from './AppLoader.vue'
import AppCard from './AppCard.vue' 
import AppForm from './AppForm.vue';
export default {
  data() {
    return {
      tags: [],
      results: [],
      people: [],
      loading: false,
      isLoaded: false,
    }
  },
  methods: {
    constructing(value, text) {
      this.tags = []
      this.tags.push(value, text)
      this.results.push([...this.tags])
    },
    async loadComments() {
      this.loading = !this.loading
      this.isLoaded = !this.isLoaded
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.people = Object.keys(data).map(key => {
        return {
          id: key,
          ...data[key]
        }
      })
      this.loading = !this.loading
    }
  },
  components: {
    AppCard,
    AppForm,
    AppLoader
  }
}
</script>
