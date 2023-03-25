<template>
  <div class="stopwatchs">
    <StopWatch v-for="block in blocks" :key="block"></StopWatch>
    <button class="add__block" v-on:click="addBlocks">+</button>
  </div>
</template>

<script>
import StopWatch from './components/StopWatch.vue';
import { ref } from 'vue';
export default {
  name: 'App',
  components: {
    StopWatch
  },
  setup() {
    let blocks = ref(3);

    function addBlocks() {
      blocks.value++;
    }
    return {
      blocks,
      addBlocks
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.stopwatchs {
  max-width: 1024px;
  margin: 0 auto;
  display: grid;
  justify-items: center;
  gap: 50px;
}

.add__block {
  width: 225px;
  height: 120px;
  background: #696969;
  border: none;
  font-size: 40px;
  color: #9E9E9E;
  cursor: pointer;
}

@media screen and (min-width: 320px) {
  .stopwatchs {
    grid-template-columns: repeat(1, 1fr);
  }
}

@media screen and (min-width: 768px) {
  .stopwatchs {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 1024px) {
  .stopwatchs {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
