<script setup>
    import { ref } from 'vue';
    import ScoreModalComponent from './ScoreModalComponent.vue';
    import InputComponent from './InputComponent.vue';
    const { modals } = defineProps(['modals']);

    const score = ref(0);

    const selectAnswer = (answer, modal) => {
        modal.selectedAnswer = answer;

    };

    const goToNextQuestion = (modalIndex) => {
    const modal = modals[modalIndex];
    if (modal.selectedAnswer) {
        if (modalIndex < modals.length - 1) {
            modal.status = 'answered';
            modals[modalIndex + 1].status = 'active';
        }
    } else {
        modal.showAlert = true;
    }
};

    const goToPreviousQuestion = (modalIndex) => {
        if (modalIndex > 0) {
            modals[modalIndex].status = 'answered';
            modals[modalIndex - 1].status = 'active';
            modals[modalIndex -1].showAlert = false;
        }
    };

    const InputStatus = ref(false);

    const goToNextModal = (modalIndex) => {
        if (modals[modalIndex].selectedAnswer) {
            if(modalIndex === 2) {
                modals[modalIndex].status = 'answered';
                InputStatus.value = !InputStatus.value
                modals.forEach(modal => {
                if (modal.selectedAnswer === modal.CorrectAnswer) {
                    score.value++;
                }
            });
            }
        }  else {
        modals[modalIndex].showAlert = true;
    }
    }
</script>

<template>
    <form action="" method="post" id="survey-form">
            <div class="modal-content" v-for="(modal, index) in modals" :key="index" v-show="modal.status === 'active'">
                <h2>Wiosna nadchodzi - konkurs Mediaflex</h2>
                <h3 class="h3-margin">Pytanie {{index + 1}}/3</h3>
                <h4>{{modal.question}}</h4>

                <div class="answers">
                    <div class="answer" v-for="(answer, answerIndex) in ['A', 'B', 'C']" :key="answerIndex">
                        <img class="image_answer" :src="modal.selectedAnswer === answer ? '/icons/flower-icon-color.svg' : '/icons/flower-icon.svg'" alt="Flower Icon">
                        <p>{{answer}}</p>
                        <input class="border-two input-color" type="button" :value="modal['answer' + answer]" :class="{ 'border-click': modal.selectedAnswer === answer }" @click="selectAnswer(answer, modal)">
                    </div>
                </div>

                <div class="buttons">
                    <div class="last-question" :class="{'invisible': index === 0}">
                        <button type="button" class="back" @click="goToPreviousQuestion(index)"><img src="/icons/back-icon.svg" alt="Back Icon"><p>Poprzednie Pytanie</p></button>
                    </div>
                    <p class="alert-one" v-show="modal.showAlert">Prosimy zaznaczyć odpowiedź</p>
                    <div class="next-question" :class="{'next-question-one': index === modals.length - 1}">
                        <InputComponent v-if="modal.status === 'active' && index === modals.length - 1"  @click="goToNextModal(index)" />
                        <button class="submit" type="button" v-else @click="goToNextQuestion(index)"><p class="paragraph">Następne Pytanie</p> <img src="/icons/next-icon.svg" alt="Next Icon"></button>
                    </div>
                </div>
            </div>
        <ScoreModalComponent v-show="InputStatus" :score="score"/>
    </form>
</template>

    
<style scoped>

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