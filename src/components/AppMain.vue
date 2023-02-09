<script>
import AppCard from './AppCard.vue';
export default {
    name:'AppMain',
        data() {
            return {
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

<div v-for="film in filmList" class="col-2 mt-5" >
    <AppCard :film="film"></AppCard>
</div>

</template>

<style lang="scss" scoped>

</style>
