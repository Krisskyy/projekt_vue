<script setup>
const { boxes } = defineProps(['boxes']);
</script>

<template>
    <div class="box" v-for="(box, index) in boxes" :key="index">
        <div class="box-header">
            <div class="box-round">
                <img :src="box.image" alt="Step One Icon">
            </div>
            <h3>Krok {{ index + 1}}</h3>
        </div>
        <div class="box-text">
            <p>{{box.title}}</p>
        </div>
    </div>
</template>

<style scoped>
    .box{
    position: relative;
    width: 400px;
    height: 285px;
    background: #FBF9F5 0% 0% no-repeat padding-box;
    box-shadow: 0px 6px 10px #CCC6B677;
    border: 4px solid #D6C092;
    opacity: 0.8;
    margin-bottom: 50px;
    border-right: none;
}

.box::before{
    content: '';
    position: absolute;
    top: -4px;
    right: -36px;
    background: #FBF9F5 0% 0% no-repeat padding-box;

    width: 0;
    height: 0;
    border-top: 142px solid transparent;
    border-left: 40px solid #FBF9F5;
    border-bottom: 143px solid transparent;
}

.box::after{
    content: '';
    position: absolute;
    top: -4px;
    right: -40px;
    background: #FBF9F5 0% 0% no-repeat padding-box;
    z-index: -1;

    width: 0;
    height: 0;
    border-top: 142px solid transparent;
    border-left: 40px solid #D6C092;
    border-bottom: 143px solid transparent;
}

.box-header{
    display: flex;
    align-items: center;
    margin: 30px 0 50px 35px;
}

.box-header h3{
    font: normal normal 35px/40px Poppins;
    color: #543E3C;
    font-size: 35px;
}


.box-round{
    display: flex;
    background: #DDC1BC 0% 0% no-repeat padding-box;
    width: 96px;
    height: 96px;
    border-radius: 100%;
    align-items: center;
    justify-content: center;
    margin-right: 30px;
}


.box-text{
    margin: 0 0 30px 35px;
    font: normal normal bold 28px/40px Poppins;
    color: #2D645A;
    font-size: 28px;
}
</style>