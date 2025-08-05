<script setup>
import { onMounted } from 'vue';
defineEmits(['wybor-levelu1','wybor-levelu1-focus']);

const props = defineProps({
ifButtonOnFocusLevelOne: Boolean
});

onMounted(() => {
    const elementToFocus = document.querySelector(".level-one-button")
    if (elementToFocus&&props.ifButtonOnFocusLevelOne===true) {
        elementToFocus.focus();
    }

})
</script>

<template>
    <div class="tlo-level1" role="img" aria-label="Wybór poziomu">
        <h1 class="sr-only">Wybór poziomu</h1>
        <div class="container">
        <button class="level-one-button my-button-2" @click="$emit('wybor-levelu1')" @keydown.enter="$emit('wybor-levelu1-focus')" role="button" 
         >Poziom 1</button>
        <button class="level-two-button" role="img" aria-label="poziom 2 niedostępny" aria-disabled ="true" disabled>Poziom 2</button>
        </div>
    </div>
   

</template>

<style scoped>
.tlo-level1 {
    background-image: url("../assets/plansza_poziom1_wybor.png");
    background-size: 1920px 1080px;
    height: 1080px;
    width: 1920px;
    top: 0px;
    left: 0px;
    position: absolute;
   
}

.container{
 
 display: flex;
 height: 1080px;
 align-items: center;
 justify-content: space-evenly;
}

.sr-only{
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

.level-one-button {
    color: rgb(29, 56, 80);
    font-size: 6.3em;
    font-style: bold;
    font-weight: 700;
    font-family: "Proxima Nova", sans-serif;
    background-size: 595px 200px;
    background-position: -1px -1px;
  
   
    /* left: 220px; */
    width: 6.1em;
    height: 2em;
    border: 4px solid rgb(0, 187, 255);
}

.level-one-button:hover {
    cursor: pointer;
}

.level-one-button:focus {
    outline: 5px solid #08e926;
}

.level-two-button {
    background-image: url("../assets/poziom2_nieaktywny.png");
    color: rgb(29, 56, 80);
    font-size: 6.3em;
    font-style: bold;
    font-weight: 700;
    font-family: "Proxima Nova", sans-serif;
    background-size: 600px 200px;
    background-position:  3px -1px;

    /* left: 1063px; */
    width: 6.1em;
    height: 2em;
    border: 4px solid rgb(0, 187, 255);
}

.my-button-2 {
  transition: 0.2s ease-out;
}

/* .my-button-2::after {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  inset: 0;
  height: 130%;
  width: 110%;
  box-sizing: border-box;
} */

.my-button-2:hover {
  cursor: pointer;
  transform: scale(1.1);
}
</style>