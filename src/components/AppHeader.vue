<script>
    import axios from 'axios';
    import { store } from '../store'
    export default {
        name : 'AppHeader',
    

    data() {
        return {
            store,
            apiUrl : 'https://api.themoviedb.org/3/search/movie',
            apiKey : '4c2c925074dfd974675224d92a594272',
        }
    },
    methods: {
        getMovies(querySearch){
                axios.get(this.apiUrl,{
                    params: {
                       api_key : this.apiKey,
                       query : querySearch,
                    }
                })
                .then((response) => {
                    console.log(response.data.results);
                    store.moviesList = response.data.results;
                    
                })
                .catch(function (error){
                    console.log(error)
                })
    },
  }
}
</script>

<template >
    <nav>
        <input type="search" v-model="store.searchMovie">
        <button @click="getMovies(store.searchMovie)">cerca</button>
    </nav>
</template>

<style lang="">
    
</style>