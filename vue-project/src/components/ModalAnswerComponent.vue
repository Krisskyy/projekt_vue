<script setup>
import { ref } from 'vue';
import { modals } from "./Modals";;
const modalsData = ref(modals);
</script>
<template>
    <div class="answer"  v-for="(modal, index) in modalsData" :key="index">
        <img class="image_answer" src="/icons/flower-icon.svg" alt="Flower Icon"> 
        <p>A</p>
        <input type="button" :value="modal.answerA" class="border-two input-color">
    </div>
</template>


<style scoped>
    .answer{
        display: flex;
        align-items: center;
        position: relative;
        height: 75px;
        margin-bottom: 20px;
    }

    .answer img{
        position: absolute;
        z-index: -1;
        left: 0;
        top: 0;
    }

    .answer p{
        color: white;
        font: normal normal bold 24px/26px Roboto;
        margin: 0 56px 0 26px;
    }

    .answer input{
        border-radius: 10px;
        width: 909px;
        background: #FFFFFF;
        padding: 10px;
        text-align: left;
        font-family: 'Poppins';
        font-size: 18px;
        cursor: pointer;
    }
</style>