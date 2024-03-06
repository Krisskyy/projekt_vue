<script setup>
const { toggleContainers } = defineProps(['toggleContainers']);
</script>

<template>
    <input class="to-survey" type="button" value="BIORĘ UDZIAŁ" @click="toggleContainers">
</template>

<style scoped>
    .to-survey{
    background: #E1B9B5 0% 0% no-repeat padding-box;
    color: #543E3C;
    border: none;
    border-radius: 51px;
    padding: 21px 30px;
    font: normal normal 600 21px Poppins;
    letter-spacing: 0.21px;
    cursor: pointer;
}
</style>