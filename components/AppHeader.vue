<template>
  <div class="common-container">
    <nav>
      <div class="site-title">
        <a href="/"><h1>Puppeteer Scraping API</h1></a>
        <p>Find Your Favorite Site You Scrape With Puppeteer</p>
      </div>
      <ul>
        <li><a href="/">Lists</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/lists/create">Add</a></li>
        <li><a href="/logout">Log out</a></li>
        <li><a href="/signup">Sign Up</a></li>
        <li><a href="/login">Log in</a></li>
      </ul>
    </nav>
  </div>
</template>
<script lang="ts">
import { defineComponent, useContext } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const { $axios } = useContext()

    const login = async () => {
      const result = await $axios.$get('http://localhost:3000/api/v1/products')
      console.log(result, 'result')
    }
    return { login }
  },
})
</script>

