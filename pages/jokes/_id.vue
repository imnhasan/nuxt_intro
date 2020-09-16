<template>
  <div>
    <nuxt-link to="/jokes">Back To Jokes</nuxt-link>
    <h1>{{ joke }}</h1>
    <hr />
    <small>Joke Id: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      joke: {},
    }
  },
  async created() {
    const config = {
      headers: {
        Accept: 'application/json',
      },
    }
    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      )
      this.joke = res.data.joke
      console.log(this.joke)
    } catch (e) {
      console.log(e)
    }
  },
  head() {
    return {
      title: this.joke,
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
