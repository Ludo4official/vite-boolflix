<script>
import AppCard from './AppCard.vue';
export default {
    name:'AppMain',
        data() {
            return {
                films: []
            }
            
        },

    components: {
        AppCard,
    },
    props: {
        filmList: {
            type: Array,
            default: []
        }
    }
}
</script>

<template>

    <div class="my-main mt-5">
        <div class="cards d-flex flex-wrap">
            <h4 v-for="filmList in films">{{ filmList.original_title }}</h4>
            <AppCard></AppCard>
        </div>
    </div>

</template>

<style lang="scss" scoped>

</style>
