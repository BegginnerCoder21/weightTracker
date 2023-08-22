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
const weightChartE1 = ref(null);
import Chart from 'chart.js/auto';
import{ nextTick, ref, shallowRef, watch } from 'vue';
const weightCart = shallowRef(null);
import WeigthHistory from '@/components/WeigthHistory.vue';
const props = defineProps<{
    weights:typeWeight[]
}>();


watch(props.weights,(weightValue) => {
    const ws = [...weightValue];

    if(weightCart.value){
        weightCart.value.data.labels =  ws.sort((a,b) => a.date - b.date ).
                map((w) => new Date(w.date).toLocaleDateString()).slice(-7);

        weightCart.value.data.datasets[0].data =  ws.map((w) => w.weight ).slice(-7);

        weightCart.value.update();
        return;
    }
    nextTick(() => {
        weightCart.value = new Chart(weightChartE1.value,{
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
                maintAspectRatio:false
            }
        })
    })
 },{deep:true});


</script>

<style scoped>

</style>