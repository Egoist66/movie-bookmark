<script setup lang="ts">
import { useMoviesStore } from '@/stores/movies';


import Movie from '@/components/features/Movie.vue'
import { computed, ref } from 'vue';
import Search from '@/components/features/Search.vue';

const m_store = useMoviesStore()

const isWatched = ref<boolean>(false)
const search = ref<string>('')
const computedMoviesKey = computed(() => isWatched.value ? 'watchedMovies' : 'movies')

</script>

<template>
  <section>

    <div class="tabs">

      <button 
        :class="{ active: m_store.activeTab === 1 }"
        @click="m_store.setActiveTab(1)"
        class="btn btn-primary">Favourite
      </button>
      <button 
        :class="{ active: m_store.activeTab === 2 }" 
        @click="m_store.setActiveTab(2)"
        class="btn btn-primary"
       >
        Search
      </button>

      <button 
        :disabled="m_store.activeTab === 2"
        @click="isWatched = !isWatched"
        class="btn btn-primary"
       >
        {{ isWatched ? 'All' : 'Watched' }}
      </button>



    </div>

    <div v-if="m_store.activeTab === 1" class="movies">

        
      <h3 class="py-3">Movies - {{ m_store.totalMovies }}</h3>
      <h3 class="py-3">Watched movies - {{ m_store.totalWatchedMovies }}</h3>

      <template v-if="m_store[computedMoviesKey].length">

        <template :key="movie.id" v-for="movie in m_store[computedMoviesKey]">
          <Movie  :movie="movie" />
        </template>

      </template>

      <template v-else>
        No movies
      </template>
     

    </div>


    <div v-else class="search">

      <h3 class="py-3">Search Movies</h3>

      <Search v-model:search="search" />

    </div>

  </section>
</template>


<style lang="css" scoped>
.btn_green {
  background: #37df5c;
}

.tabs {
  display: flex;
  gap: 10px;
  padding-bottom: 20px;
}

.active {
  background: #37df5c;
}
</style>