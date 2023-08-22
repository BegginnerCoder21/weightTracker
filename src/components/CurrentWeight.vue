<template>
    <div>
        <div class="current-box">
            <span>{{ props.currentWeight.weight }}</span>
            <small>current weight (Kg)</small>
        </div>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    currentWeight:{weight:number}
}>();

</script>

<style scoped>

.current-box{
    background-color: white;
    border-radius: 50%;
    height: 170px;
    width: 170px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    border: 4px solid hotpink;
}
.current-box small{
    background-color: white;
    font-size: 12px;
    font-style: italic;
    color: gray;
}
.current-box span{
    background-color: white;
    font-size: 30px;
    font-weight: bold;
}

</style>