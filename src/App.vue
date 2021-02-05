<template>
  <div id="app">
    <v-table/>
    <p>Hello</p>
  </div>
</template>

<script>

import vTable from './components/v-table'
import {mapActions, mapGetters} from 'vuex'

export default {
  name: 'app',
  components: {
    vTable
  },
  data: () => {
    return {}
  },
  computed: {
    ...mapGetters([
      'USERS'
    ])
  },
  methods: {
    ...mapActions([
      'GET_USERS_FROM_API'
    ])
  },
  mounted() {
    this.GET_USERS_FROM_API()
  }
}
</script>

<style lang >
</style>


