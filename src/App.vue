<script>
import { store } from './components/store.js';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  name:'App',
  data() {
    return {
      store,
      films: []
    }
  },

  created() {
          axios
            .get('https://api.themoviedb.org/3/movie/popular?api_key=01bbd11fd4dcd85ddf948c39bbf9f20a&language=en-US')
            .then((response) => {
                this.films = response.data.results.slice(0,12)
                console.log(response.data.results)
            })
  },

  methods: {
      reactToSearchFilm() {
          
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
  <div class="my-cnt">
    <div class="container text-light my-cnt">
        <div class="row">
          <div class="col">
            <AppHeader @searchFilm="reactToSearchFilm"></AppHeader>
          </div>
        </div>
        <div class="row">
            <AppMain :filmList="films"></AppMain>
        </div>
        <div class="row">
          <div class="col">
            <AppFooter></AppFooter>
          </div>
        </div>
    </div>
  </div>
</template>

<style lang="scss">

@import './components/styles/partials/main.scss';

.my-cnt {
  background-color: black;
}

</style>
