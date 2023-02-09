<template>
    <div class="list">
        <article v-for="(pokemon, index) in pokemons" :key="'poke'+index">
            <h3>{{  pokemon.name }}</h3>
        </article>
    </div>
</template>

<script>

    export default {
        props: [
            'imageUrl',
            'apiUrl'
        ],
        data: () => {
            return{
                pokemons: []
            }
        },
        methods: {
            fetchData() {
                let req = new Request(this.apiUrl)
                fetch(req).then((resp) => {
                    if(resp.status === 200){
                        return resp.json()

                    }
                }).then((data) => {
                    this.nextUrl = data.next
                    data.results.forEach(pokemon => {
                        this.pokemons.push(pokemon)
                    });

                }).catch((error) => {
                    console.log(error)
                })
            }
        },
        created() {
            this.fetchData()
        }
    }
</script>

<style lang="scss" scoped>

</style>