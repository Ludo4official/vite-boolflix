<script>
import { store } from './components/store.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  name:'App',
  data() {
    return {
      store
    }
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter
  }
}
</script>

<template>
<AppHeader></AppHeader>
<AppMain></AppMain>
<AppFooter></AppFooter>
</template>

<style lang="scss">
@import './components/styles/partials/main.scss';
</style>
