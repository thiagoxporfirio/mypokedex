<template>
    <div class="detail">
        <div class="detail-view" v-if="show">

        </div>
        <i v-else class="fas fa-spinner fa-spin"></i>
    </div>
</template>

<script>
export default {
    props: [
        'pokemonUrl',
        'imageUrl'
    ],

    data: () => {
        return {
            show: false,
            pokemon: {}
        }
    },
    methods: {
        fetchData() {
            let req = new Request(this.pokemonUrl);
            fetch(req)
                .then((resp) => {
                    if (resp.status === 200)
                        return resp.json();
                })
                .then((data) => {
                    this.pokemon = data
                    this.show = true
                    
                })
                .catch((error) => {
                    console.log(error);
                })
        }
    },

    created() {
        this.fetchData()
    }
}
</script>

<style lang="scss" scoped>

.detail{
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
    position: fixed;
    top: 0;
    left: 0;
    padding: 90px 10px 10px;
    
}

</style>