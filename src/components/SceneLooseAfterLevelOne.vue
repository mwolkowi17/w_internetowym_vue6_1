<script setup>
import { ref, onMounted } from 'vue';
defineEmits(['jeszcze-raz', 'jeszcze-raz-focus', 'koniec-gry']);

const props = defineProps({
    ifButtonOnFocus: Boolean
});

onMounted(() => {
    const elementToFocus = document.querySelector(".gram-jeszcze-1")
    if (elementToFocus && props.ifButtonOnFocus === true) {
        elementToFocus.focus();
    }

})

const przegrana_sound = new Audio(new URL('../assets/przegrana_gra.mp3', import.meta.url).href);
przegrana_sound.play();
</script>

<template>
    <div class="plansza-lose">
        <div class="container">
            <h2 class="naglowek">Niestety przegrałeś.</h2>
            <h2 class="napis">Chcesz spróbować jeszcze raz?</h2>
            <div class="container-buttons">
                <button class="gram-jeszcze-1 my-button anim1" @click="$emit('jeszcze-raz')"
                    @keydown.enter="$emit('jeszcze-raz-focus')" role="button">Zagraj jeszcze raz</button>
                <button class="zakoncz-gre my-button anim1" @click="$emit('koniec-gry')" role="button">Zakończ
                    grę</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.plansza-lose {
    background-image: url("../assets/przegrana_plansza.png");
    background-size: 1920px 1080px;
    height: 1080px;
    width: 1920px;
    top: 0px;
    left: 0px;
    position: absolute;
    z-index: 2;
}

.container {
    display: flex;
    flex-direction: column;
    height: 1080px;
    justify-content: center;
    align-items: center;
}

.naglowek {
    color: rgb(255, 255, 255);
    font-size: 6.25em;
    font-style: bold;
    font-weight: 600;
    font-family: "Proxima Nova", sans-serif;
    margin-bottom: 0px;
    /* top: 140px;
    left: 500px; */
    height: 88px;
    width: 333px;
    display: flex;
    justify-content: center;
    z-index: 2;
    white-space: nowrap;
}

.napis {
    color: rgb(255, 255, 255);
    font-size: 4.4em;
    font-style: bold;
    font-weight: 400;
    font-family: "Proxima Nova", sans-serif;
    white-space: nowrap;
    margin-bottom: 1.5em;
    /* top: 340px;
    left: 450px; */
    height: 88px;
    width: 333px;
    display: flex;
    justify-content: center;
    z-index: 2;
}

.container-buttons {
    display: flex;
    height: 200px;
    align-items: center;
    justify-content: space-evenly;
}


.gram-jeszcze-1 {
    /* background-image: url("../assets/gram_jeszcze_raz_button.png"); */
    color: rgb(29, 56, 80);
    font-size: 3.8em;
    font-style: bold;
    font-weight: 700;
    font-family: "Proxima Nova", sans-serif;
    background-size: 583px 192px;
    background-position: -1px -2px;
    margin-right: 2em;
    /* top: 650px;
    left: 300px; */
    width: 583px;
    height: 192px;
    z-index: 3;
    border: 4px solid rgb(0, 187, 255);
}

.gram-jeszcze-1:hover {
    cursor: pointer;
}

.gram-jeszcze-1:focus {
    /* outline: thick double #08e926; */
    outline: 5px solid #08e926;
}

.zakoncz-gre {
    /* background-image: url("../assets/zakoncz_gre_button.png"); */
    color: rgb(29, 56, 80);
    font-size: 3.8em;
    font-style: bold;
    font-weight: 700;
    font-family: "Proxima Nova", sans-serif;
    background-size: 583px 192px;
    background-position: -1px -2px;

    /* top: 650px;
    left: 1020px; */
    width: 583px;
    height: 192px;
    z-index: 3;
    border: 4px solid rgb(0, 187, 255);
}

.zakoncz-gre:hover {
    cursor: pointer;
}

.zakoncz-gre:focus {
    /* outline: thick double #08e926; */
    outline: 5px solid #08e926;
}

/* The animation code */
@keyframes example {

    /* from {background-color: red;}
  to {background-color: yellow;} */
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