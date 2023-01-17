<script>
    import axios from 'axios';
    import { store } from '../store'
    import MovieCard from './MovieCard.vue';
    export default {
        name : 'AppHeader',
    components:{
        MovieCard,
    },

    data() {
        return {
            store,
            apiUrlMovies : 'https://api.themoviedb.org/3/search/movie',
            apiUrlSeries :  'https://api.themoviedb.org/3/search/tv',
            apiKey : '4c2c925074dfd974675224d92a594272',
        }
    },
    methods: {
        getMovies(querySearch){
                axios.get(this.apiUrlMovies,{
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

                axios.get(this.apiUrlSeries,{
                    params: {
                       api_key : this.apiKey,
                       query : querySearch,
                    }
                })
                .then((response) => {
                    console.log(response.data.results);
                    store.seriesList = response.data.results;
                    
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
        <img src="../assets/img/logo.webp" alt="">
        <div class="input-gg">
            <input type="text" class="" v-model="store.searchMovie" >
            <button class="btn btn-primary" @click="getMovies(store.searchMovie)">cerca</button>
        </div>
    </nav>
    <div class="cards-wrapper">
        <MovieCard/>
    </div>
</template>

<style lang="scss">
    nav{
        display: flex;
        padding: 1rem;
        background-color: black;

        img{
            width: 100px;
        }
    }

</style>