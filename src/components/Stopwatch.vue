<script setup>
import { ref } from 'vue';
import { useStopwatch } from 'vue-timer-hook';

const autoStart = false;
const stopwatch = useStopwatch(autoStart);
const isOn = ref(false);
stopwatch.reset();
stopwatch.pause();

</script>

<template>
    <div class="container">
        <div class="time" :class="{active: isOn}">
            <div class="time-text">
                <span v-if="stopwatch.hours.value !== 0">{{stopwatch.hours}}</span>
                <span v-if="stopwatch.hours.value != 0">:</span>
                <span v-if="stopwatch.minutes.value != 0">{{stopwatch.minutes}}</span>
                <span v-if="stopwatch.minutes.value != 0">:</span>
                <span>{{stopwatch.seconds}}</span>
            </div>    
        </div>
        <div class="controls" :class="{active: isOn}">
            <button v-if="!isOn" @click="{
                stopwatch.start();
                isOn = true;
                }">
                <svg class="btn" :class="{active: isOn}" width="17" height="20" viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 20V0L17 10L0 20Z" fill="#9E9E9E"/>
                </svg>
            </button>
            
            <button v-if="isOn" @click="{
                stopwatch.pause();
                isOn = false;
            }">
                <svg class="btn" :class="{active: isOn}" width="17" height="20" viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect x="7" width="3" height="20" fill="white"/>
                    <rect width="3" height="20" fill="white"/>
                </svg>
            </button>
            <button @click="{
                stopwatch.reset();
                stopwatch.pause();
                isOn = false;
            }">
                <svg class="btn" :class="{active: isOn}" width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect width="20" height="20" fill="#9E9E9E"/>
                </svg>
            </button>
        </div>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center ;
    width: 225px;
    height: 120px;
    background-color: #696969;
}

.controls {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 50%;
    gap: 42px;
}

.time {
    font-family: Gotham Pro;
    font-size: 22px;
    font-weight: 400;
    line-height: 21px;
    letter-spacing: 0em;
    text-align: center;
    color: #9E9E9E;
    border-bottom: 1px solid #9E9E9E;
    width: 100%;
    height: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.active {
    color: #FFF;
    border-color: #FFF;
    filter: brightness(0) saturate(100%) invert(100%) sepia(0%) saturate(7500%) hue-rotate(70deg) brightness(99%) contrast(107%);
    
}

button {
    background-color: transparent;
    border: none;
}

.btn {
    filter: brightness(0) saturate(100%) invert(76%) sepia(14%) saturate(20%) hue-rotate(21deg) brightness(81%) contrast(92%);
}


</style>

