<template>
    <div v-if="props.weights.length > 0">
        <h2>Last 7 days</h2>
        <div class="canvas-box">
            <canvas ref="weightChartE1"></canvas>
        </div>
        <WeigthHistory :weights="weights" />
    </div>
</template>

<script setup lang="ts">
import type typeWeight from '@/types';
import { ref } from 'vue';
import WeigthHistory from '@/components/WeigthHistory.vue';
const props = defineProps<{
    weights:typeWeight[]
}>()
const weightChartE1 = ref(null)

</script>

<style scoped>

</style>