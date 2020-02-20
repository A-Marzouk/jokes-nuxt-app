<template>
    <div>
        <h1>
            Single joke | <nuxt-link to="/jokes">Back to jokes</nuxt-link>
        </h1>
        <hr>
        <p>
            {{joke.joke}}
        </p>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        data(){
            return{
                joke:{},
            }
        },
        async mounted() {
            const config = {
                headers:{
                    'Accept' : 'application/json'
                }
            };
            const res = await axios.get('https://icanhazdadjoke.com/j/' + this.$route.params.id,config);
            this.joke = res.data ;
        },
    }
</script>

<style>

</style>
