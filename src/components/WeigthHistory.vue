<template>
    <div>
        <h2>History Weight  </h2>
        <ul >
            <li v-for="weight in props.weights">
                <span>{{ weight.weight }}</span>
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

</style>