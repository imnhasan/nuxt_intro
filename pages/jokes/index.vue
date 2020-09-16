<template>
  <div class="container mx-auto">
    <div class="mt-4 mb-4">
      <SearchJokes v-on:search-text="searchText" />
    </div>
    <!-- Six columns -->
    <div class="container">
      <div class="flex flex-wrap">
        <div v-for="joke in jokes" :key="joke.id" class="ml-4">
          <Joke :id="joke.id" :joke="joke.joke" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Joke from '../../components/Joke'
import SearchJokes from '../../components/SearchJokes'

export default {
  components: {
    Joke,
    SearchJokes,
  },
  data() {
    return {
      jokes: [],
    }
  },
  async created() {
    const config = {
      headers: {
        Accept: 'application/json',
      },
    }
    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config)
      this.jokes = res.data.results
      console.log(this.jokes)
    } catch (e) {
      console.log(e)
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: 'application/json',
        },
      }
      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        )
        this.jokes = res.data.results
        console.log(this.jokes)
      } catch (e) {
        console.log(e)
      }
    },
  },
  head() {
    return {
      title: 'Jokes',
      meta: [
        {
          hid: 'Description',
          name: 'nhasan',
          content: 'Best place for learn',
        },
      ],
    }
  },
}
</script>
