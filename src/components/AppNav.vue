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
        <li class="text-sm inline-block p-3 text-gray-800">
          <router-link :to="{ name: 'login' }">Sign in</router-link>
        </li>
        <li class="text-sm inline-block p-3 text-gray-800">
          <router-link :to="{ name: 'home' }">Account</router-link>
        </li>
      </template>
      <template v-if="authenticated">
        <li class="text-sm inline-block p-3 text-gray-800">
          <router-link :to="{ name: 'home' }">Account</router-link>
        </li>
        <li class="text-sm inline-block p-3 text-gray-800">
          <router-link :to="{ name: 'home' }">Log out</router-link>
        </li>
      </template>
    </ul>
  </header>

</template>

<script>
import {mapGetters} from 'vuex'

export default {
  computed: {
    ...mapGetters({
      authenticated: 'auth/authenticated',
      user: 'auth/user'
    })
  }
}
</script>
