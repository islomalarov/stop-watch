<template>
    <div class="stopwatch__block">
        <div class="stopwatch__block-info">
            <span class="hours">{{ hours }}</span> : <span class="hours">{{ minuts }}</span> : <span class="hours">{{ seconds }}</span>
        </div>
        <div class="stopwatch__block-control">
            <button class="stopwatch__block-btn" v-if="isPlay" v-on:click="play"><img src="../assets/icons/треугольник.png"
                    alt=""></button>
            <button class="stopwatch__block-btn" v-if="isPaused" v-on:click="pause"> <img src="../assets/icons/Пауза.png"
                    alt=""></button>
            <button class="stopwatch__block-btn"> <img src="../assets/icons/квадрат.png" alt=""></button>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue';
export default {
    name: "StopWatch",
    setup() {
        let hours = ref(0);
        let minuts = ref(0);
        let seconds = ref(0)
        let isPlay = ref(true);
        let isPaused = ref(false);
        let interval;

        const startTimer = () => {
            seconds.value++;

            if(seconds.value > 60) {
                minuts.value++;
                seconds.value = 0
            }
            if(minuts.value> 60) {
                hours.value++;
                minuts.value = 0
            }
        }


        function play() {
            isPlay.value = false;
            isPaused.value = true
            interval = setInterval(startTimer, 10)
        }
        function pause() {
            clearInterval(interval)
            isPaused.value = false;
            isPlay.value = true;
        }
        return {
            hours,
            minuts,
            seconds,
            isPlay,
            isPaused,
            play,
            pause,
        }
    }
}

</script>

<style scoped>
.stopwatch__block {
    width: 225px;
    height: 120px;
    background: #696969;
}

.stopwatch__block-info {
    height: 60px;
    border-bottom: 1px solid #9E9E9E;
    ;
}

.stopwatch__block-control {
    display: flex;
    justify-content: space-between;
    padding: 20px 70px;
}

.stopwatch__block-btn {
    background: none;
    border: none;
    cursor: pointer;
}
</style>