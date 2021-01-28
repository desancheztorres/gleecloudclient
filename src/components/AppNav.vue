<template>
  <header class="flex flex-wrap md:flex-nowrap items-center justify-between mb-6 -mx-3 -mt-3">
    <ul class="flex items-center">
      <li>
        <router-link :to="{ name: 'home' }" class="text-sm inline-block p-3 text-gray-800">Home</router-link>
      </li>
      <li>
        <a href="" class="text-sm inline-block p-3 text-gray-800">Your files</a>
      </li>
    </ul>
    <ul class="flex items-center">
      <template v-if="!authenticated">
        <li>
          <router-link :to="{ name: 'login' }" class="text-sm inline-block p-3 text-gray-800">Sign in</router-link>
        </li>
        <li>
          <a href="#" class="text-sm inline-block p-3 text-gray-800">Account</a>
        </li>
      </template>
      <template v-if="authenticated">
        <li>
          <a href="#" class="text-sm inline-block p-3 text-gray-800">Account</a>
        </li>
        <li>
          <a href="#" class="text-sm inline-block p-3 text-gray-800" @click.prevent="logout">Log out</a>
        </li>
      </template>
    </ul>
  </header>

</template>

<script>
import {mapGetters, mapActions} from 'vuex'

export default {
  computed: {
    ...mapGetters({
      authenticated: 'auth/authenticated',
      user: 'auth/user',
    })
  },
  methods: {
    ...mapActions({
      logoutAction: 'auth/logout'
    }),
    async logout() {
      await this.logoutAction()

      this.$router.replace({ name: 'home' })
    }
  }
}
</script>
