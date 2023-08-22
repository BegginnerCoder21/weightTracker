<template>
    <div v-if="props.weights.length > 0">
        <h3>Last 7 days</h3>
        <div class="canvas-box">
            <canvas ref="weightChartE1"></canvas>
        </div>
        <WeigthHistory :weights="weights" />
    </div>
</template>

<script setup lang="ts">
import type typeWeight from '@/types';
const weightChartE1 = ref(null);
import Chart from 'chart.js/auto';
import{ nextTick, ref, shallowRef, watch } from 'vue';
const weightChart = shallowRef(null);
import WeigthHistory from '@/components/WeigthHistory.vue';
const props = defineProps<{
    weights:typeWeight[]
}>();


watch(props.weights,(weightValue) => {
    const ws = [...weightValue];

    if(weightChart.value){
        weightChart.value.data.labels =  ws.sort((a,b) => a.date - b.date ).
                map((w) => new Date(w.date).toLocaleDateString()).slice(-7);

        weightChart.value.data.datasets[0].data =  ws.map((w) => w.weight ).slice(-7);

        weightChart.value.update();
        return;
    }
    nextTick(() => {
        weightChart.value = new Chart(weightChartE1.value.getContext('2d'),{
            type:'line',
            data:{
                labels:ws.sort((a,b) => b.date - a.date ).
                map((w) => new Date(w.date).toLocaleDateString() ),
                datasets:[{
                    label:'Weight',
                    data:ws.sort((a,b) => b.date - a.date ).map((w) => w.weight ),
                    backgroundColor: 'rgba(255, 105, 180, 0.2)',
					borderColor: 'rgba(255, 105, 180, 1)',
					borderWidth: 1,
					fill: true
                }]
            },
            options:{
                responsive:false,
                maintainAspectRatio:false
            }
        })
    })
 },{deep:true});


</script>

<style scoped>

h3{
    color: gray;
}

.canvas-box {
	width: 100%;
	max-width: 720px;
	background-color: white;
	padding: 1rem;
	border-radius: 0.5rem;
	box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
	margin-bottom: 2rem;
    margin-top: 10px;
}
</style>