<template>
  <div>
    <div
      class="hero bg-gray-400"
      :style="`background:url(${backgroundImage}); background-size:cover`"
    >
      <div
        class="container mx-auto flex flex-col md:flex-row items-end-pd-8"
        style="height: 350px"
      >
        <div class="w-full md:w-1/4"></div>
        <div class="w-full md:w-3/4 md:ml-12">
          <h1 class="font-heading text-white text-2xl">{{ game.name }}</h1>
          <div class="text-white">{{ game.platforms[0].name }}</div>
        </div>
      </div>
    </div>
    <div class="container mx-auto flex flex-col md:flex-row">
      <div class="md:w1/4 -mt-16">
        <img
          :src="game.cover.url.replace('t_thumb', 't_cover_big')"
          alt="cover"
          class="mb-8"
        />
        <div class="md-4">
          <span class="font-semibold">Platfroms:</span>
          <span v-for="platfrom in game.platfroms" :key="platfrom.id">{{
            platfrom.name
          }}</span>
        </div>
        <div class="md-4">
          <span class="font-semibold">Released:</span>
          <span>{{ new Date(game.first_release_date).toDateString() }}</span>
        </div>
        <div class="md-6">
          <a :href="getOfficialWebsite">Official Website</a>
        </div>
        <div v-if="game.total_rating" class="md-10">
          <div class="text-5xl">{{ Math.round(game.total_rating) }}%</div>
          <div class="font-semibold">Overall Rating</div>
        </div>
      </div>
      <div class="md:w-3/4 md:ml-12 py-8 leading-normal">
        <p class="md-12 mb-4">{{ game.summary }}</p>
        <div class="flex flex-wrap -mx-4">
          <a
            v-for="screenshot in game.screenshots"
            :key="screenshot.cloudinary_id"
            href="#"
            class="w-full md:w-1/4 px-4 md-12 no-underline"
          >
            <img
              :src="screenshot.url.replace('t_thumb', 't_screenshot_med')"
              alt="screenshots"
            />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  asyncData({ params, error }) {
    const proxyurl = 'https://cors-anywhere.herokuapp.com/'
    return axios
      .get(
        `${proxyurl}https://api-v3.igdb.com/games/${params.id}/?fields=name,cover.url,summary,platforms.name,first_release_date,websites,total_rating,screenshots.url,total_rating&expand=platforms,screenshots,cover`,
        {
          headers: {
            'user-key': 'd7e6544670a8b6ef4f81dba61c76fe95',
            'X-Requested-With': 'XMLHttpRequest',
          },
        }
      )
      .then((res) => {
        console.log(res.data[0])
        return {
          game: res.data[0],
        }
      })
      .catch((e) => {
        console.log(e)
      })
  },
  computed: {
    getOfficialWebsite() {
      return '#'
    },
    backgroundImage() {
      return this.game.screenshots[0].url.replace('t_thumb', 't_1080p')
      // return 'data:image/jpeg;base64,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'
    },
  },
  head() {
    return {
      title: this.game.name + ' | Video Games',
    }
  },
}
</script>
