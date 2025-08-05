<script setup>
import { ref, onMounted } from 'vue'
import { instrukcjaTekst } from '../lib/instrukcja';
defineEmits(['koniec-instrukcja', 'koniec-instrukcja-focus'])

const props = defineProps({
  ifButtonOnFocus: Boolean
});

onMounted(() => {
  const elementToFocus = document.querySelector(".dalej")
  //dodanie warunku propsu
  if (elementToFocus && props.ifButtonOnFocus === true) {
    elementToFocus.focus();
  }

})

// const textToDisplay ="Znajdujesz się w Wirtualnej Dżungli - aby ją przejść, musisz odpowiedzieć "+
//        " prawidłowo na pytania dotyczące internetu. Gra składa się z dwóch"+
//         " poziomów. Rzucasz kostką i posuwasz się do przodu o tyle pól, ile oczek"+
//         " wyrzuciła kostka. Na początku gry otrzymujesz trzy szanse.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"+
//         " Na polach oznaczonych znakiem zapytania &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; czeka Cię pytanie." + 
//         " Każda błędna odpowiedź - to strata 1 szansy. Utrata wszystkich szans" + 
//         " oznacza zakończenie gry. Dobra odpowiedź - to kolejny rzut kostką" + 
//         " Po drodze czekają Cię zasadzki kryjące się na polach oznaczonych" + 
//         " wykrzyknikiem &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;. Powodzenia!"

const textToDisplay ="Znajdujesz się w Wirtualnej Dżungli - aby ją przejść, musisz odpowiedzieć "+
       " prawidłowo na pytania dotyczące internetu. Gra składa się z dwóch"+
        " poziomów. Rzucasz kostką i posuwasz się do przodu o tyle pól, ile oczek"+
        " wyrzuciła kostka. Na początku gry otrzymujesz trzy szanse &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"
        
const textToDisplay2 = ".  Na polach oznaczonych znakiem zapytania &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"

const textToDisplay3 = "czeka Cię pytanie." + " Każda błędna odpowiedź - to strata 1 szansy. Utrata wszystkich szans" + 
        " oznacza zakończenie gry. Dobra odpowiedź - to kolejny rzut kostką." + 
        " Po drodze czekają Cię zasadzki, kryjące się na polach oznaczonych" + 
        " wykrzyknikiem &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"

const textToDisplay4 = ". Powodzenia!"
</script>
<template>
  <div class="tlo1" aria-label="Zasady gry">
    <div class="container">
    <h1 class="instrukcja-title">Zasady gry</h1>
    <div class="kontener-instrukcja">
    
         <span class="instrukcja"  v-html="textToDisplay"></span>
         <img class="gwiazdka" alt="" src="../assets/ikona1gwiazdka.png" />
          <span class="instrukcja"  v-html="textToDisplay2"></span>
         <img class="pytajnik" alt="" src="../assets/ikona2question.png"/>
          <span class="instrukcja"  v-html="textToDisplay3"></span>
         <img class="wykrzyknik" alt="" src="../assets/ikona3wykrzyknik.png" />
         <span class="instrukcja"  v-html="textToDisplay4"></span>
    </div>
      <button class="dalej anim1" @click="$emit('koniec-instrukcja')" @keydown.enter="$emit('koniec-instrukcja-focus')"
    role="button">Dalej</button>
  </div>
</div>

</template>

<style scoped>
.tlo1 {
  background-image: url("../assets/plansza_zasady_gry.png");
  background-size: 1920px 1080px;
  height: 1080px;
  width: 1920px;
  top: 0px;
  left: 0px;
  position: absolute;
  /* display: flex; */
}

.container{
  display: flex;
    flex-direction: column;
  height: 1080px;
  justify-content:center;
  align-items: center;
}
.instrukcja-title{
  /* position: absolute; */
    color: rgb(255, 255, 255);
  font-size: 6.9em;
  font-style: normal;
  font-weight: 400;
  font-family: "Proxima Nova", sans-serif;
  margin: 0px;
  /* line-height: 1.5; */
  /* top: 5px;
  left: 705px; */
}

/* .kontener-instrukcja {
  display: flex;
  align-items: center;
  padding: .5rem 1rem;
   width: 1300px; 
  width: 1400px;
  top: 210px;
  left: 260px;
  position: absolute;
} */

.kontener-instrukcja {
  /* display: flex;
  align-items: center; */
  display: inline-block;
  padding: .5rem 1rem;
  /* width: 1300px; */
  height: 565px;
  width: 1400px;
  overflow: auto;
  /* top: 210px;
  left: 260px; */
  /* position: absolute; */
}

.instrukcja {
  color: rgb(255, 255, 255);
  /* font-size: 41px; */
  font-size: 2.4em;
  font-style: normal;
  font-weight: 300;
  font-family: "Proxima Nova", sans-serif;
  line-height: 1.7;
  position: relative;

}

/* .instrukcja:focus{
   outline:  0px solid #9a009e !important;
} */

.gwiazdka{
  position: relative;
  /* top: 220px;
  left: 746px; */
  margin-top: -2.8em;
  margin-right: -95px;
  left: -98px;
  top:35px
  
}

.pytajnik{
  position: relative;
   /* top: 283px;
  left: 355px; */
    margin-top: -2.4em;
  margin-right: -80px;
  left: -90px;
  top:35px
}

.wykrzyknik{
  position: relative;
  /* top: 475px;
  left: 715px; */
    margin-top: -2.4em;
  margin-right: -80px;
  left: -90px;
  top:35px
}

.dalej {
  /* background-image: url("../assets/przycisk_dalej_imie.png"); */
  color: rgb(29, 56, 80);
  font-size: 4.3em;
  font-style: bold;
  font-weight: 700;
  font-family: "Proxima Nova", sans-serif;
  /* position: absolute; */
  /* top: 820px;
  left: 850px; */
  width: 4em;
  height:1.5em;
  border: 4px solid rgb(0, 187, 255);
  /* display: flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  overflow: hidden;           /* Prevent overflow *
  transform-origin: center;  */
  transition: .2s ease-in-out;
  margin-top: -0.3em;

}

.dalej:hover {
  cursor: pointer;
  transform: scale(1.1);
}

.dalej:focus {
  /* border: 4px solid #08e926; */
  /* outline: thick double #08e926; */
  outline: 5px solid #08e926;
}

/* The animation code */
@keyframes example {

  from {
    opacity: 0;
  }

  to {
    opacity: 100;
  }
}

/* The element to apply the animation to */
.anim1 {
  animation-name: example;
  animation-duration: 1s;
}
</style>