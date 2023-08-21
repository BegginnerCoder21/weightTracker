<template>
    <div>
         <form @submit.prevent="$emit('add-weight',weightInput)">
            <input type="text" v-model="weightInput">
            <input type="submit" value="add weight">
        </form>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';


const weightInput = ref<number>(0);

</script>

<style scoped>

</style>