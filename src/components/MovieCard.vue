<script>
    import "/node_modules/flag-icons/css/flag-icons.min.css";
    import { store } from '../store'
    export default {
        data() {
            return {
                store,
                //lang : `` 
            }
        },
    }
</script>

<template >
    <div class="movie-card">
        <ul>
            <li v-for="movieEl in store.moviesList">
                <h2>{{ movieEl.title }}</h2>
                <h3>Titolo originale: {{ movieEl.original_title }}</h3>
                <span :class="(movieEl.original_language != null) ? 'fi fi-'+movieEl.original_language : ''"></span> 
                <span :class="(movieEl.original_language === 'en') ? 'fi fi-us' : ''"></span>
                <p>Star: {{ movieEl.vote_average }}</p>
            </li>
        </ul>
        
        <ul>
            <li v-for="serieEl in store.seriesList">
                <h2>{{ serieEl.name }}</h2>
                <h3>Titolo originale: {{ serieEl.original_name }}</h3>
                <span :class="(serieEl.original_language != null) ? 'fi fi-'+serieEl.original_language : ''"></span> 
                <span :class="(serieEl.original_language === 'en') ? 'fi fi-us' : ''"></span>
                <p>Star: {{ serieEl.vote_average }}</p>
            </li>
        </ul>
    </div>
</template>

<style lang="scss">
    .movie-card{
        display: flex;
    
    ul{
        list-style-type: none;
    }
}
</style>