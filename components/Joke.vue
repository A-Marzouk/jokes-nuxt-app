<template>
    <div class="joke">
        <nuxt-link :to="'/jokes/' + id"> {{ joke }}</nuxt-link>
    </div>
</template>

<script>
    export default {
        name:'Joke',
        props:['joke','id']
    }
</script>

<style>
    .joke{
        padding: 1rem;
        border: 1px dotted grey;
        margin: 1rem 0;
    }
</style>
