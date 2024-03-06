<script setup>
const { cards } = defineProps(['cards']);

</script>

<template>
        <div class="card" v-for="{image, title, description} in cards">
            <div class="image">
                <div class="round"></div>
                <img :src="image" :alt="title">
            </div>
            <div class="card-text">
                <h3>{{title}}</h3>
                <p>{{description}}</p>
            </div>
        </div>
</template>

<style scoped>
.card{
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    position: relative;
    background: #FBF9F5 0% 0% no-repeat padding-box;
    border: 4px solid #D6C092;
    border-radius: 4px;
    width: 380px;
    height: 411px;
    box-shadow: 0px 6px 10px #CCC6B677;
    opacity: 0.8;
}


.image{
    display: flex;
    position: relative;
    justify-content: center;
    text-align: center;

}

.card-text{
    padding: 30px 35px;
}

.round{
    position: absolute;
    background: #DDC1BC 0% 0% no-repeat padding-box;
    width: 135px;
    height: 135px;
    border-radius: 100%;
    z-index: -1;
    left: 67px;
    bottom: 4px;
}

.card h3{
    text-align: left;
    font: normal normal bold 28px Poppins;
    color: #2D645A;
    opacity: 1;
}
</style>