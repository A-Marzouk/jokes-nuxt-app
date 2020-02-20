<template>
    <div>
        <h1>
            Jokes
        </h1>

        <div v-for="joke in jokes" :key="joke.id">
            <joke :joke="joke.joke" :id="joke.id" />
            <hr>
        </div>

    </div>
</template>

<script>
    import axios from 'axios'
    import joke from '../../components/Joke'

    export default {
        components:{
          joke
        },
        head() {
            return {
                title: 'Dad jokes',
                meta: [
                    {
                        hid: 'description',
                        name: 'description',
                        content: 'best place for jokes'
                    }
                ]
            }
        },
        data() {
            return {
                jokes: []
            }
        },
        async created() {
            const config = {
                headers: {
                    'Accept': 'application/json'
                }
            };
            try {
                const res = await axios.get('https://icanhazdadjoke.com/search', config);
                console.log(res.data);
                this.jokes = res.data.results;
            } catch (e) {
                console.log(e);
            }

        }
    }
</script>

<style lang="scss">

</style>
