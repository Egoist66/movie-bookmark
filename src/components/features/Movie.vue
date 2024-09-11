<script setup lang="ts">
import { useMoviesStore, type Movies } from '@/stores/movies';


const { movie } = defineProps<{ movie: Movies }>()
const {toggleWatched, deleteMovie} = useMoviesStore()




</script>


<template>
  
    <div class="movie shadow">
        <img :src="'https://www.svgrepo.com/show/508699/landscape-placeholder.svg'" :alt="movie.original_title"
            class="movie-img" />
        <div class="p-3">
            <div class="movie-name">
                {{ movie.original_title }} ({{ movie.release_date }})
            </div>
            <span class="movie-overview">{{ movie.overview }}</span>
            <div class="movie-buttons">
                <button @click="toggleWatched(movie.id)" class="btn movie-buttons-watched">
                    <span v-if="!movie.isWatched">Watch</span>
                    <span v-else>Reset</span>
                </button>
                <button @click="deleteMovie(movie.id)" class="btn movie-buttons-delete">Delete</button>
            </div>
        </div>
    </div>


</template>



<style scoped>
.movie {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    margin-bottom: 20px;
    padding: 10px;
    border-radius: 10px;
}

.movie-accept {
    margin-right: 10px;
}

.movie-img {
    width: 200px;
    height: 200px;
    object-fit: cover;
    border-radius: 50%;
}

.movie-name {
    display: flex;
    align-items: center;
    font-size: 20px;
    margin-bottom: 20px;
}

.movie-overview {
    display: block;
    margin-bottom: 20px;
}

.movie-buttons {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.movie-buttons-watched {
    color: #fff;
    flex-grow: 1;
    background: #1eb4c3;
}

.movie-buttons-watched__icon {
    width: 15px;
    margin-left: 10px;
}

.movie-buttons-delete {
    color: #fff;
    flex-grow: 1;
    background: #ff2a2a;
}


</style>