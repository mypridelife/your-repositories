<template>
  <div class="page">
    <group>
      <x-input v-model="authToken" title="Your AuthToken" type="password" />
    </group>
    <br>
    <x-button type="primary" @click.native="handleLogin">登录</x-button>
    <x-button @click.native="handleGen">generate your token</x-button>
  </div>
</template>

<script>
import * as types from '@/store/mutation-types'
export default {
  data() {
    return {
      authToken: '',
      msg: ''
    }
  },
  mounted() {
    this.$store.commit(types.TITLE, 'Login')
  },
  methods: {
    handleLogin() {
      if (this.authToken) {
        this.$store.commit(types.LOGIN, this.authToken)
        // const redirect = decodeURIComponent(this.$route.query.redirect || '/')
        this.$router.replace({
          path: 'userInfo'
        })
      }
    },
    handleGen() {
      window.open('https://github.com/settings/tokens/new', '_blank')
    }
  }
}
</script>

<style scoped>
</style>
