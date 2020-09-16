<template>
  <div>
    <AppHeader />
    <nuxt />
  </div>
</template>

<script>
// import axios from 'axios'
import AppHeader from '~/components/AppHeader'

// axios.defaults.headers.common['user-key'] = 'd7e6544670a8b6ef4f81dba61c76fe95'
// axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'

export default {
  components: {
    AppHeader,
  },
}
</script>
