<script setup>

</script>

<template>
          <div class="first-page">
            <header class="padding">
                <img class="logo" src="./icons/logo.svg" alt="logo">
                <a href="#awards">Co możesz wygrać</a>
                <a href="#steps">Co zrobić aby wygrać</a>
            </header>
    
            <div class="main-area padding">
                <section class="banner">
                    <div class="left">
                        <h2>Wiosna nadchodzi - zgarnij wiosenne gadżety od Mediaflex!</h2>
                        <div class="line"></div>
                        <p>Do wiosny jeden krok... weź udział w konkursie i wygraj gadżety, które z pewnością umilą coraz cieplejsze wiosenne popołudnia.</p>
                        <input class="to-survey" type="button" value="BIORĘ UDZIAŁ">
                    </div>
                    <div class="right">
                        <img src="./icons/flowers.svg" alt="flowers">
                    </div>
                </section>
                <div class="round"><img src="./icons/mouse-icon.svg" alt="Mouse Icon"></div>
            </div>
        </div>
</template>

<style scoped>


  /* CSS do headera */
  header{
      display: flex;
      height: 110px;
      border-bottom: 1px solid #DDC1BC;
      align-items: center;
  }

  header a{
      font: normal normal 18px/35px 'Poppins';
      text-decoration: none;
      color: black;
  }

  header a:first-of-type{
      margin-right: 52px;
  }


  .logo{
      margin-right: 690.65px;
  }

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

.left input, .second-page input, .third-page input{
    background: #E1B9B5 0% 0% no-repeat padding-box;
    color: #543E3C;
    border: none;
    border-radius: 51px;
    padding: 21px 30px;
    font: normal normal 600 21px Poppins;
    letter-spacing: 0.21px;
    cursor: pointer;
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

.padding{
      padding-left: 303px;
      padding-right: 286px;
  }
</style>
