<script>
export default {
    name:'AppCard',
    data() {
        return {
            
        }
    },

    props: {
        film: Object
    },

    methods: {
      getNewVote() {
        let newVote = this.film.vote_average;
        newVote = newVote / 2;
        newVote = Math.ceil(newVote);
        console.log(newVote);

        return newVote;
      },

      countryFlag(lang) {

        switch (lang) {
          case 'en':
            lang = 'uk';
            break;
        }
        let flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;
        return flag;
      }
    }
}
</script>

<template>

    <div class="flip-box mb-5 px-3">
        <div class="flip-box-inner">
            <div class="flip-box-front">
                <img class="img-fluid" :src=" `https://image.tmdb.org/t/p/w342${film.poster_path} `" alt="">
            </div>
            <div class="flip-box-back">
                <h5>{{ film.original_title }}</h5>
                <h6>{{ film.title }}</h6>
                <h6>
                    <span v-for="n in getNewVote()">★</span>
                    <span v-for="n in (5 - getNewVote())">☆</span>
                </h6>
                <img :src="countryFlag(film.original_language)" alt="">
                <p>{{ film.overview }}</p>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>

.flip-box {
  background-color: transparent;
  width: 250px;
  height: 400px;
}
.flip-box-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
  
}

.flip-box:hover .flip-box-inner {
  transform: rotateY(180deg);
}

.flip-box-front, .flip-box-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-box-front {
  color: black;
}

.flip-box-back {
  color: white;
  transform: rotateY(180deg);
}

</style>
