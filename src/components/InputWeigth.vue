<template>
    <div class="input-box">
         <form @submit.prevent="$emit('add-weight',weightInput)">
            <input type="number" step="0.1" v-model="weightInput">
            <input type="submit" value="add weight">
        </form>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';


const weightInput = ref<number>(0);

</script>

<style scoped>

input[type=submit]{
    background-color: hotpink;
    color: white;
    border: none;
    border-radius: 0px 5px 5px 0px;
    padding: 7px;
    cursor: pointer;
    font-weight: 700;
    font-size: 13px;
}   

input[type=number]{
    height: 29px;
    width: 230px;
    border: 1.5px solid gray;
    outline: none;
    border-radius: 5px 0px 0px 5px;
    padding: 5px;
    margin-top: 30px;
    border-right-color: hotpink;
    
}

input[type=number]:focus{
    border: 1.5px solid hotpink;
}
input[type=number]:hover{
    border: 2px solid hotpink;
}


.input-box{
    margin-bottom: 30px;
}
</style>