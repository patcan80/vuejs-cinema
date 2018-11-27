<template>
    <div id="movie-list">
        <div v-if="filteredMovies.length">
            <movie-item v-for="movie in filteredMovies" v-bind:movie="movie.movie"></movie-item>
        </div>
        <div v-else-if="movies.length" class="no-results">
            No Results.
        </div>
        <div v-else class="no-results">
            Loading....
        </div>
    </div>
</template>

<script>
    import MovieItem from './MovieItem.vue'
    export default {
        name: "MovieList",
        props: [ 'genre', 'time', 'movies' ],
        methods: {
            moviePassesGenreFilter(movie){
                if (!this.genre.length){
                    return true;
                } else {
                    return this.genre.find(genre => movie.genre === genre);
                }

            }
        },
        computed: {
            filteredMovies() {
                return this.movies.filter(this.moviePassesGenreFilter);
            }
        },
        components: {
            MovieItem
        },
        created(){
            
        }
    }
</script>

<style scoped>

</style>
