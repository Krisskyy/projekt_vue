<script setup>
    import ModalAnswerComponent from './ModalAnswerComponent.vue';
    import { ref } from 'vue';

    const modals = ref([
        {
            question: 'W którym roku powstal Mediaflex?',
            answerA: '2007',
            answerB: '2008',
            answerC: '2009',
            status: 'one'
        },
        {
            question: 'Firmową wartością nie jest:',
            answerA: 'Jakość',
            answerB: 'Rozsądek',
            answerC: 'Komunikacja',
            status: 'two'
        },
        {
            question: 'Biuro Mediaflex znajduje się w:',
            answerA: 'Krakowie',
            answerB: 'Szczecinie',
            answerC: 'Rzeszowie',
            status: 'three'
        }
    ]);

    const choice = () => ({

    });
</script>


<template>
    <div class="modal-content" v-for="(modal, index) in modals" :key="index">
        <h2>Wiosna nadchodzi - konkurs Mediaflex</h2>
        <h3 class="h3-margin">Pytanie {{index + 1}}/3</h3>
        <h4>{{modal.question}}</h4>

        <div class="answers">
                 <div class="answer"><img class="image_answer" src="/icons/flower-icon.svg" alt="Flower Icon"> <p>A</p> <input class="border-two input-color" type="button" :value="modal.answerA"></div>
                 <div class="answer"><img class="image_answer" src="/icons/flower-icon.svg" alt="Flower Icon"> <p>B</p> <input class="border-two input-color" type="button" :value="modal.answerB"></div>
                 <div class="answer"><img class="image_answer" src="/icons/flower-icon.svg" alt="Flower Icon"> <p>C</p> <input class="border-two input-color" type="button" :value="modal.answerC"></div>

            <div class="buttons">
                <div class="last-question" :class="{'invisible': modal.status == 'one'}">
                    <button type="button" class="back"><img src="/icons/back-icon.svg" alt="Back Icon"><p>Poprzednie Pytanie</p> </button>
                </div>
                <p class="alert-one">Prosimy zaznaczyć odpowiedź</p>
                <div class="next-question next-question-one">
                    <button class="submit" type="button" v-if="modal.status == 'three'"><p class="paragraph">ZAKOŃCZ QUIZ</p> <img src="/icons/next-icon.svg" alt="Next Icon"></button>
                    <button class="submit" type="button" v-else><p class="paragraph">Następne Pytanie</p> <img src="/icons/next-icon.svg" alt="Next Icon"></button>
                </div>
            </div>
        </div>
    </div>
</template>
    
<style scoped>
.modal-content{
    position: absolute;
    z-index: 1;
    width: 1088px;
    height: 600px;
    background: #FFFFFF 0% 0% no-repeat padding-box;
    box-shadow: 0px 3px 60px #101E0033;
    border-radius: 20px;
    top: 180px;
    left: 416px;
    padding: 40px 40px 40px 35px;
}

.modal-content h2{
    color: #2D635A;
    font: normal normal normal 38px/51px Abril Fatface;
}

.modal-content h3{
    color: #E1B9B5;
    font: normal normal 600 21px/28px Poppins;
}

.h3-margin{
    margin-top: 13px;
    margin-bottom: 19px;
}

.modal-content h4{
    font: normal normal  20px/26px Poppins;
    margin-bottom: 48px;
}

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

.next-question{
    display: flex;
    justify-content: flex-end;
    width: 33%;
}

.last-question{
    width: 33%;
}

.submit{
    display: flex;
    color: #543E3C;
    justify-content: center;
    align-items: center;
    background: #E1B9B5 0% 0% no-repeat padding-box;
    box-shadow: 0px 3px 6px #00000029;
    border-radius: 40px;
    width: 256px;
    height: 61px;
    padding: 18px 32px;
    border: none;
    text-transform: uppercase;
    font-weight: 600;
    cursor: pointer;
}


.paragraph{
    margin-right: 10px;
    font: normal normal 600 18px/27px Poppins;
    color: #543E3C;
}


.buttons{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.back{
    display: flex;
    align-items: center;
    width: 190px;
    height: 19px;
    font: normal normal 16px/19px Roboto;
    letter-spacing: 0px;
    color: #E1B9B5;
    cursor: pointer;
}

.back p{
    margin-left: 15px;
}

</style>