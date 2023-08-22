<template>
    <div class="app">
        <h1>Weight Tracker</h1>
        <CurrentWeight :currentWeight="currentWeight" />
        <InputWeigth @add-weight="addWeight" />
        <WeigthChart :weights="weights" />
    </div>
</template>

<script setup lang="ts">
import{ computed,ref} from 'vue';
import type typeWeight from '@/types';
import CurrentWeight from '../components/CurrentWeight.vue';
import WeigthChart from '../components/WeigthChart.vue';
import InputWeigth from '../components/InputWeigth.vue';

const currentWeight = computed<{
    weight:number
}>(() => {
    return weights.value.sort((a,b) => b.date - a.date )[0] || {weight:0};
});
const weights = ref<typeWeight[]>([]);
 const addWeight = (weightInput:number) =>   {
    weights.value.push({
        weight:weightInput,
        date:new Date().getTime()
    })
 }


</script>

<style scoped>
.app{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

h1{
    margin-bottom: 30px;
    font-weight: bold;
}

</style>