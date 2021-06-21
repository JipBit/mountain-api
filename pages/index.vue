<template>
  <div class="container">
    <h1 class="font-extrabold text-5xl text-black dark:text-white text-center my-6">Mountain API</h1>

    <div class="flex flex-wrap m-4">
      <div v-for="post in post" :key="post" class="xl:w-1/4 md:w-1/2 p-4">
        <div class="bg-gray-100 dark:bg-gray-800 p-6 rounded-lg">
          <img class="h-40 rounded w-full object-cover object-center mb-6" :src='post.image' alt="content">
          <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">{{ post.continent}}: {{ post.countries[0]}} {{ post.countries[1]}}</h3>
          <h2 class="text-lg text-gray-900 dark:text-white font-medium title-font mb-4">{{ post.title }}</h2>
          <p class="leading-relaxed text-base text-gray-700 dark:text-gray-200">{{ post.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    async asyncData({ $axios }) {
      const post = await $axios.$get('https://api.nuxtjs.dev/posts')
      return { post }
    }
  }
</script>

<style>
body{
  @apply dark:bg-gray-900;
}
</style>
