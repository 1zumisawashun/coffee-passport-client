<template>
  <div class="common-container">
    <div class="login-form">
      <h2>Log in</h2>
      <label for="email" class="login-label">Email</label>
      <input
        v-model="user.email"
        type="text"
        name="email"
        required
        class="login-input"
      />
      <div class="email error"></div>
      <label for="password" class="login-label">Password</label>
      <input
        v-model="user.password"
        type="password"
        name="password"
        required
        class="login-input"
      />
      <div class="password error"></div>
      <button class="login-button" @click="login">Log in</button>
      <button class="login-button signup-button">Sign Up</button>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, useContext, reactive } from '@nuxtjs/composition-api'
type User = {
  email: string
  password: string
}
const initUser = {
  email: '',
  password: '',
}
export default defineComponent({
  layout: 'auth',
  setup() {
    const { $axios } = useContext()
    const user = reactive<User>(initUser)

    const login = async () => {
      console.log(user, 'user')
      const result = await $axios.$post(
        'http://localhost:3000/api/v1/users/login',
        user
      )
      console.log(result, 'result')
    }
    return { login, user }
  },
})
</script>