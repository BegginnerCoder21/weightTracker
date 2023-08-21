<template>
    <div>
        <div>
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

</style>