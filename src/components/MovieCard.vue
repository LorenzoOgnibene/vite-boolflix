<script>
    import "/node_modules/flag-icons/css/flag-icons.min.css";
    import { store } from '../store'
    export default {
        data() {
            return {
                store,
                imgUrl : 'https://image.tmdb.org/t/p/w342',
            }
        },
        methods: {
            getImgPath(imgPath){
                return (`${this.imgUrl}${imgPath}`);
            }
        },
    }
</script>

<template >
    <div class="movie-card">
        <div class="container">
            <div class="row">
                <div  v-for="movieEl in store.moviesList" class="col-6 col-md-3 single-card">
                    <img class="img-fluid" :src="movieEl.poster_path != null ? getImgPath(movieEl.poster_path) : 'https://m.media-amazon.com/images/I/51qqz9h3bYL._SL1409_.jpg'" alt="ciao" >
                    <h2>{{ movieEl.title }}</h2>
                    <h3>Titolo originale: {{ movieEl.original_title }}</h3>
                    <span :class="(movieEl.original_language != null) ? 'fi fi-'+movieEl.original_language : ''"></span> 
                    <span :class="(movieEl.original_language === 'en') ? 'fi fi-us' : ''"></span>
                    <p>Star: {{ movieEl.vote_average }}</p>
                </div>
                <div v-for="serieEl in store.seriesList" class="col-6 col-md-3 single-card">
                    <img class="img-fluid" :src="serieEl.poster_path != null ? getImgPath(serieEl.poster_path) : 'https://m.media-amazon.com/images/I/51qqz9h3bYL._SL1409_.jpg' " alt="ciao">
                    <h2>{{ serieEl.name }}</h2>
                    <h3>Titolo originale: {{ serieEl.original_name }}</h3>
                    <span :class="(serieEl.original_language != null) ? 'fi fi-'+serieEl.original_language : ''"></span> 
                    <span :class="(serieEl.original_language === 'en') ? 'fi fi-us' : ''"></span>
                    <p>Star: {{ serieEl.vote_average }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .movie-card{
        display: flex;
        flex-wrap: wrap;

    ul{
        list-style-type: none;
    }

    img{
        width: 342px;
        height: 512px;
    }
}
    //.single-card{
      //  width: calc(100% / 4);
    //}
</style>