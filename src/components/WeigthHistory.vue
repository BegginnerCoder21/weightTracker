<template>
    <div class="history-box"> 
        <h3>History Weight  </h3>
        <ul >
            <li v-for="weight in props.weights">
                <span>{{ weight.weight }}Kg</span>
                <small>{{ new Date(weight.date).toLocaleDateString() }}</small>
            </li>
        </ul>

    </div>
</template>

<script setup lang="ts">
import type typeWeight from '@/types';


const props = defineProps<{
    weights:typeWeight[]
}>()
</script>

<style scoped>

.history-box{
    margin-top: 30px;
}

h3{
    color: gray;
}

ul{
    margin-top: 20px;
}

ul li{
    list-style: none;
    margin-top: 6px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
ul li span{
    font-weight: bold;

}
ul li small{
    color: gray;

}

</style>