<template>
    <div class="searchbar">
        <form @submit.prevent="setPokemonUrl">
            <input type="text" v-model="searchvalue">
        </form>
        <i class="fas fa-search" @click="setPokemonUrl"></i>
    </div>
</template>

<script>
export default {
    props: [
        'apiUrl'
    ],
    data: () => {

        return {
            searchvalue: '',

        }
    },
    methods: {

        setPokemonUrl(url) {
            if (this.searchvalue !== '')
                this.$emit('setPokemonUrl', this.apiUrl + this.searchvalue);
        }

    }
}
</script>

<style>

</style>