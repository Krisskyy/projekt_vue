<script setup>
import  HeaderComponent from './components/HeaderComponent.vue';
import  ButtonComponent from './components/ButtonComponent.vue';
import  CardComponent   from './components/CardComponent.vue';
import  BoxComponent    from './components/BoxComponent.vue';
import  FooterComponent from './components/FooterComponent.vue';
</script>

<template>
  <div class="container">
    <div class="first-page">
      <HeaderComponent />
      <div class="main-area padding">
                <section class="banner">
                    <div class="left">
                        <h2>Wiosna nadchodzi - zgarnij wiosenne gadżety od Mediaflex!</h2>
                        <div class="line"></div>
                        <p>Do wiosny jeden krok... weź udział w konkursie i wygraj gadżety, które z pewnością umilą coraz cieplejsze wiosenne popołudnia.</p>
                        <ButtonComponent />
                    </div>
                    <div class="right">
                        <img src="/icons/flowers.svg" alt="flowers">
                    </div>
                </section>
                <div class="round"><img src="/icons/mouse-icon.svg" alt="Mouse Icon"></div>
            </div>
    </div>

      <div class="second-page padding">
            <h2 id="awards" class="heading">Co możesz wygrać?</h2>
            <div class="cards">
              <CardComponent/>
            </div>
              <ButtonComponent/>
            <a href="#">Regulamin konkursu</a>
      </div>
      
      <div class="third-page padding">
            <h2 id="steps">Do Nagrody Dzielą Cię 3 Kroki!</h2>
            <div class="boxes">
              <BoxComponent/>
            </div>
            <ButtonComponent/>
      </div>

      <FooterComponent/>
  </div>
</template>

<style scoped>
@import url(./assets/main.css);

/* First page */
.first-page{
    background: #FBF9F5 0% 0% no-repeat padding-box;
    max-width: 1920px;
    height: 1080px;
}

.banner{
    display: flex;
    align-items: center;
    padding-top: 73px;
}

.left h2{
    text-align: left;
    color: #2D645A;
    font-family: 'Abril Fatface';
    font-weight: 100;
    font-size: 42px;
}

.left .line{
    width: 193px;
    margin: 30px 0;
    border: 1.5px solid #ebbe45;
}

.left p{
    width: 586px;
    font: normal normal normal 18px/32px Poppins;
    text-align: left;
    margin-bottom: 50px;
}

.round{
    display: flex;
    justify-content: center;
    align-items: center;
    background: #E1B9B5 0% 0% no-repeat padding-box;
    border-radius: 100%;
    width: 60px;
    height: 60px;
    margin: auto;
    margin-top: 304px;
}

/* Second Page */
.second-page{
    height: 918px;
    margin-top: 100px;
}

.cards{
    display: flex;
    justify-content: space-between;
}

.heading, .third-page h2{
    color: #543E3C;
    font-size: 48px;
    font-weight: bold;
    margin-bottom: 50px;
}


.second-page a{
    display: flex;
    text-align: left;
    text-decoration: underline;
    font: normal normal 600 21px/117px Poppins;
    letter-spacing: 0.21px;
    color: #543E3C;
    justify-content: center;
    margin-top: 40px;
    margin-bottom: 100px;
}

/* Third page */
.third-page{
    background: #FBF9F5 0% 0% no-repeat padding-box;
    padding-bottom: 100px;
}

.third-page h2{
    padding-top: 100px;
}

.boxes{
    display: flex;
    justify-content: space-between;
}
</style>
