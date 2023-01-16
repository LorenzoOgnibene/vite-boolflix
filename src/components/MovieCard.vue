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
            </li>
        </ul>
        <span class="fi fi-xx"></span>
         
    </div>
</template>

<style lang="scss">
    ul{
        list-style-type: none;
    }
</style>