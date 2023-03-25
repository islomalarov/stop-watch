<template>
    <div class="stopwatch__block">
        <div class="stopwatch__block-info">
            <span :class="isHours ? 'hours active' : 'hours'" v-if="isHours">{{ hours > 9 ? hours : '0' + hours }} :
            </span>
            <span :class="isMinuts ? 'minuts active' : 'minuts'" v-if="isMinuts">{{ minuts > 9 ? minuts : '0' + minuts }}
                : </span>
            <span :class="isSeconds ? 'seconds active' : 'seconds'">{{ seconds > 9 ? seconds : '0' + seconds }}</span>
        </div>
        <div class="stopwatch__block-control">
            <button class="stopwatch__block-btn" v-if="isPlay" v-on:click="play"><img src="../assets/icons/треугольник.png"
                    alt="icon-1"></button>
            <button class="stopwatch__block-btn" v-if="isPaused" v-on:click="pause"> <img src="../assets/icons/Пауза.png"
                    alt="icon-2"></button>
            <button class="stopwatch__block-btn" v-on:click="reset"> <img src="../assets/icons/квадрат.png"
                    alt="icon-3"></button>
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
        let seconds = ref(0);
        let isHours = ref(false);
        let isMinuts = ref(false);
        let isSeconds = ref(false);
        let isPlay = ref(true);
        let isPaused = ref(false);
        let interval;

        function startTimer() {
            seconds.value++;

            if (seconds.value > 60) {
                minuts.value++;
                isMinuts.value = true;
                seconds.value = 0;
            }
            if (minuts.value > 60) {
                isHours.value = true;
                hours.value++;
                minuts.value = 0;
            }
        }


        function play() {
            isPlay.value = false;
            isPaused.value = true;
            isSeconds.value = true;
            clearInterval(interval);
            interval = setInterval(startTimer, 1);
        }
        function pause() {
            clearInterval(interval)
            isPaused.value = false;
            isPlay.value = true;

        }
        function reset() {
            clearInterval(interval);
            isPaused.value = false;
            isPlay.value = true;
            isHours.value = false;
            isMinuts.value = false;
            isSeconds.value = false;
            hours.value = 0;
            minuts.value = 0;
            seconds.value = 0;

        }
        return {
            hours,
            minuts,
            seconds,
            isPlay,
            isPaused,
            isHours,
            isMinuts,
            isSeconds,
            play,
            pause,
            reset
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
    border-bottom: 1px solid #9E9E9E;
    color: #9E9E9E;
    padding: 22px 0 20px 0;
}

span {
    font-weight: 400;
    font-size: 22px;
    line-height: 21px;
    text-align: center;
}

.minuts.active,
.seconds.active,
.hours.active {
    color: white;
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