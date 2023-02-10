<script>
import { store } from '../components/store.js';
import axios from 'axios';
export default {
    name:'AppHeader',
    data() {
        return {
            links: [
                'Home',
                'Serie TV',
                'Film',
                'Originali',
                'Aggiunti di recente',
                'La mia lista'
            ],

            store

        }
    },

    methods: {
        faiQualcosa() {
            axios
            .get('https://api.themoviedb.org/3/search/movie?api_key=01bbd11fd4dcd85ddf948c39bbf9f20a&query=' + this.store.nameValue)
            .then((response) => {
                this.store.films = response.data.results;
                console.log(this.store.nameValue)
            })
        }
    },
    created() {
        this.faiQualcosa();
    }

}
</script>

<template>
    <div class="my-header d-flex">
        <div class="my-img">
            <img src="https://i.pcmag.com/imagery/reviews/05cItXL96l4LE9n02WfDR0h-5.fit_scale.size_760x427.v1582751026.png" alt="">
        </div>

        <div class="my-links">
            <ul class="d-flex">
                <li v-for="link in links" class="px-2">
                    {{ link }}
                </li>
            </ul>
        </div>

        <div class="user">
            <div class="searchBar">
                <button @click="faiQualcosa()" class="my-btn">
                    Vai
                </button>
                <input v-model="store.nameValue" class="my-search" type="text" name="" id="" placeholder="Cerca">
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .my-header {
        height: 70px;
        align-items: center;
        justify-content: space-between;

        .my-img {
            height: 100%;
            width: 25%;

            img {
                height: 100%;
                width: 100%;
                object-fit: cover;
            }
        }

        .my-links {
            width: 50%;
            height: 100%;

            ul {
                list-style: none;
                height: 100%;

                li {
                    height: 100%;
                    display: flex;
                    align-items: center;
                }

                li:hover {
                    cursor: pointer;
                    font-weight: bold;
                    border-bottom: 3px solid red;
                }
            }
        }

        .user {
            width: 25%;

            .searchBar {
                width: 100%;
                height: 100%;

                .my-btn {
                    border-radius: 5px;
                    padding: 3px 15px;
                    margin-right: 5px;
                    background-color: black;
                    color: white;
                    border: 1px solid red;
                    font-weight: bold;

                    &:hover {
                        background-color: red;
                        color: #000;
                    }
                }

                .my-search {
                    background-color: black;
                    border-style: none;
                    color: white;
                }
            }
            
        }
    }
</style>