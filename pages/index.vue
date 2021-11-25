<template>
  <div>
    <Tutorial />
    <button @click="handleClick">click here!</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, useContext } from '@nuxtjs/composition-api'
export default defineComponent({
  setup() {
    const { $axios } = useContext()

    const handleClick = async () => {
      const result = await $axios.$get('http://localhost:3000/api/v1/products')
      console.log(result, 'result')
    }
    return { handleClick }
  },
})
</script>
