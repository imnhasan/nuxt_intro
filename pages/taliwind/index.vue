<template>
  <div>
    <div class="flex">
      <div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:max-w-full lg:w-1/2 lg:py-24 lg:py-12">
        <div class="xl:max-w-lg xl:ml-auto">
          <img class="h-10" src="/img/logo.svg" alt="Workstation"/>
          <img class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full sm:object-cover sm:object-center lg:hidden" src="/img/beach-work.jpg" alt="beach work" />
          <h1 class="mt-6 text-2xl font-bold text-gray-900 leading-tight sm:mt-8 sm:text-4xl lg:text-3xl xl:text-4xl">
            You can work anywhere.<br class="hidden lg:inline">
            <span class="text-indigo-500">Taking advantage of it</span>
            <p class="mt-2 text-gray-500 sm:mt-4 sm:text-xl">
              Lorem ipsum, or limps as it is sometimes known, is dummy text used in laying out print, graphic or web designs.
              The passage is attributed to an unknown typesetter in the 15th century who is thought to have scrambled parts of.
            </p>
            <div class="mt-4 sm:mt-6">
              <a href="#" class="inline-block px-5 py-3 rounded-lg shadow-lg bg-indigo-600 md:hover:bg-green-400 hover:text-3xl hover:bg-indigo-400 active:bg-indigo-600 focus:outline-none focus:shadow-outline text-sm text-white uppercase tracking-wider font-semibold sm:text-base">Book you scape</a>
            </div>
          </h1>
        </div>
      </div>
      <div class="hidden lg:block lg:w-1/2 lg:relative">
        <img class="absolute inset-0 h-full w-full lg:object-cover lg:object-center" src="/img/beach-work.jpg" alt="beach work" />
      </div>
    </div>
    <div>
      <div class="mx-w-md sm:max-w-xl lg:max-w-6xl mx-auto px-8 lg:px-12 py-8">
        <h2 class="text-xl text-gray-900">Popular Destinations</h2>
        <p class="text-gray-600">A selection of great work-friendly cities with lots to see and explore.</p>
        <div class="flex flex-wrap -mx-4">
          <div class="mt-6 w-full px-4 lg:w-1/2 xl:w-1/3" v-for="destination in popularDestinations">
            <DestinationCard :destination="destination" />
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import DestinationCard from '../../components/TailwindDestinationCard'

export default {
  name: "index",
  layout: 'tailwind',
  components: {
    DestinationCard,
  },
  data() {
    return {
      logo: '/_nuxt/assets/img/logo.svg',
      beachwork: '/img/beach-work.jpg',
      popularDestinations: [
        {
          city: 'Toronto',
          averagePrice: 120,
          propertyCount: 76,
          imageUrl: '/img/toronto.jpg',
          imageAlt: 'Toronto skyline',
        },
        {
          city: 'Malibu',
          averagePrice: 215,
          propertyCount: 43,
          imageUrl: '/img/malibu.jpg',
          imageAlt: 'Cliff in Malibu',
        },
        {
          city: 'Chicago',
          averagePrice: 130,
          propertyCount: 115,
          imageUrl: '/img/chicago.jpg',
          imageAlt: 'Chicago skyline',
        },
        {
          city: 'Seattle',
          averagePrice: 135,
          propertyCount: 63,
          imageUrl: '/img/seattle.jpg',
          imageAlt: 'Seattle skyline',
        },
        {
          city: 'Colorado',
          averagePrice: 85,
          propertyCount: 47,
          imageUrl: '/img/colorado.jpg',
          imageAlt: 'Lake in Colorado',
        },
        {
          city: 'Miami',
          averagePrice: 115,
          propertyCount: 86,
          imageUrl: '/img/miami.jpg',
          imageAlt: 'Beach in Miami',
        },
      ],
    }
  }
}
</script>
