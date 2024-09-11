<script setup lang="ts">

const model = defineModel<string>('search')

</script>


<template>
    <form @submit.prevent="console.log(model?.toUpperCase())">
        <input 
            v-model.trim="model"
            class="form-control"
            :data-value="model" 
            type="search" 
            name="search"
            placeholder="Enter query..." 
            id="search"
        >

    </form>
</template>



<style scoped></style>