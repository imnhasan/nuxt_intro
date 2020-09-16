<template>
  <div class="container mx-auto py-16">
    <h1 class="text-4xl font-heading uppercase mb-8">Popular Games</h1>
    <div class="game-container flex flex-wrap -mx-4">
      <nuxt-link
        v-for="game in games"
        :key="game.id"
        :to="'/games/' + game.id"
        class="w-full md:w-1/5 px-4 mb-12"
      >
        <img
          :src="game.cover.url.replace('t_thumb', 't_cover_big')"
          alt="cover"
        />
        <div
          class="text-black font-semisolid text-lg overflow-hidden whitespace-no-wrap"
        >
          {{ game.name }}
        </div>
        <div
          class="text-black font-semisolid text-lg overflow-hidden whitespace-no-wrap pb-1"
        >
          {{ game.genres[0].name }}
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  components: {},
  asyncData({ params, error }) {
    const proxyUrl = 'https://cors-anywhere.herokuapp.com/'
    return axios
      .get(
        `${proxyUrl}https://api-v3.igdb.com/games/?fields=name,genres.name,cover.url,popularity&order=popularity:desc&expand=genres`,
        {
          headers: {
            'user-key': 'd7e6544670a8b6ef4f81dba61c76fe95',
            'X-Requested-With': 'XMLHttpRequest',
          },
        }
      )
      .then((res) => {
        console.log(res.data)
        return {
          games: res.data,
        }
      })
      .catch((e) => {
        console.log(e)
      })
  },
  data() {
    return {
      games: [],
    }
  },

  head() {
    return {
      title: 'Game | Home',
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
