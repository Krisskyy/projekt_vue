<script setup>
import InputComponent from './InputComponent.vue'
import { ref, watchEffect } from 'vue'
const { score, NpsInvisible, toggleWindow } = defineProps(['score', 'NpsInvisible', 'toggleWindow']);
const checkedAll = ref(false);
const rules = ref(false);
const data = ref(false);
const dataTwo = ref(false);
watchEffect(() => {
  if (checkedAll.value) {
    rules.value = true;
    data.value = true;
    dataTwo.value = true;
  }
  if(!checkedAll.value) {
    rules.value = false;
    data.value = false;
    dataTwo.value = false;
  }
});
const checkboxes = ref([
    {
         id: "all",
         v: checkedAll,
         required: false,
         label: 'Zaznacz wszystkie zgody'
    },
    {
         id: "rules",
         v: rules,
         required: true,
         label: '* Akceptuję <a style="color: #E1B9B5;" href="#">regulamin konkursu</a>'
    },
    {
         id: 'data',
         v: data,
         required: false,
         label: 'Zgoda na przetwarzanie danych osobowych dla celów konkursu'
    },
    {
         id: 'dataTwo',
         v: dataTwo,
         required: true,
         label: '* Wyrażam zgodę na przetwarzanie podanych przeze mnie moich danych osobowych w zakresie imię, nazwisko, adres e-mail, numer PWZ, numer telefonu przez Administratora w celu organizacji i realizacji Konkursu.'
    }
    ]);


    const isChcecked = ref(false);
    watchEffect(() => {
    if (rules.value  && dataTwo.value) {
        isChcecked.value = !isChcecked.value;
    } else if (!checkedAll.value) {
        isChcecked.value = false;
    }
});

    function handleClick(event) {
    if (isChcecked.value) {
        event.preventDefault();
        toggleWindow();
    }
}

</script>


<template>
    <div class="modal-content score" >
        <h2>Wiosna nadchodzi - konkurs Mediaflex</h2>
        <h3>Dziękujemy za grę!</h3>
        <h4>Twój wynik: &nbsp <span class="final-result"> {{ score }}/3</span></h4>
        <p class="par">Aby grać o nagrody - zaakceptuj zgody i napisz swój wynik</p>
        <div class="images">
            <img src="/icons/prize-one.png" alt="Prize one icon">
            <img src="/icons/prize-two.png" alt="Prize two icon">
            <img src="/icons/prize-three.png" alt="Price three icon">

            <div class="score-round"></div>
        </div>

        <table>
            <tbody>
                <tr v-for="(checkbox, index) in checkboxes" :key="index">
                    <td><input type="checkbox" v-model="checkbox.v" :id="checkbox.id" class="check" :required="checkbox.required"></td>
                    <td><label :for="checkbox.id" v-html="checkbox.label"></label></td>
                </tr>
            </tbody>
        </table>
            <p>Klauzula informacyjna RODO <a href="#">czytaj więcej</a></p>
            <p>* Pola obowiązkowe są oznaczone gwiazdką</p>

            <div class="next-page">
                <InputComponent class="end-button" @click="handleClick"/>
              
            </div>
    </div>
    


</template>


<style scoped>
.modal-content.score{
    width: 1088px;
    height: 726px;
}

.score h2{
    color: #2D635A;
    font: normal normal normal 38px/51px Abril Fatface;
}

.score h3{
    width: 260px;
    height: 39px;
    font: normal normal normal 28px/42px Poppins;
    letter-spacing: 0px;
    color: #000000;
    margin: 25px 0 30px 0;
}

.score h4{
    display: flex;
    justify-content: center;
    align-items: center;
    border: 2px solid #E3E3E3;
    border-radius: 20px;
    width: 421px;
    height: 95px;
    margin-bottom: 50px;
    font-family: Poppins;
    font-size: 38px;

}

.score .par{
    width: 600px;
    height: 28px;
    font: normal normal 20px/26px Poppins;
    margin-bottom: 21px;
}

.score p:nth-of-type(2){
    margin: 13px 0 23px 0;
    font: normal normal 14px/21px Poppins;
    font-weight: 500;
}

.score p:nth-of-type(3){
    margin-bottom: 23px;
    font: normal normal 14px/21px Poppins;
    font-weight: 500;
}

.score .end-button{
    margin-bottom: 30px;
}

.score .end-button p{
    text-align: center;
    font: normal normal 600 18px/27px Poppins;
    color: #543E3C;
}


.score p a, .score td a {
    margin-left: 10px;
}

.score table input{
    width: 19px;
    height: 19px;
}

.score tr, td{
    display: flex;
    align-items: flex-start;
}

.score tr{
    margin-bottom: 15px;
}

.score table{
    height: 156px;
}

.score label{
    font: normal normal 14px/21px Poppins;
    font-weight: 500;
    margin-left: 8px;
}
.next-page{
    display: flex;
    align-items: center;
    margin: 0 0 15px 0px
}

.score span, .score a{
    color: #E1B9B5;
}

.score .images img, .score-round{
    position: absolute;
}

.score .images img:first-of-type{
    width: 77px;
    z-index: 2;
    right: 254px;
    top: 190px;
}

.score .images img:nth-of-type(2){
    width: 124px;
    z-index: 3;
    right: 145px;
    top: 205px;
}

.score .images img:last-of-type{
    width: 206px;
    right: 50px;
    top: 262px;
    z-index: 4;
}

.score-round{
    background: #DDC1BC 0% 0% no-repeat padding-box;
    width: 257px;
    height: 257px;
    border-radius: 100%;
    top: 120px;
    right: 78px;
}

.button-nps{
    display: flex;
    justify-content: center;
    align-items: center;
}

</style>