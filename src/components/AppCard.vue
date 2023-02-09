<script>
export default {
    name:'AppCard',
    data() {
        return {
            
        }
    },
    props: {
        film: Object
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
                <h3>{{ film.original_title }}</h3>
                <h5>{{ film.title }}</h5>
                <h6>{{ film.vote_average }}</h6>
                <h6>{{ film.original_language }}</h6>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>

.flip-box {
  background-color: transparent;
  width: 100%;
  height: 200px;
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
