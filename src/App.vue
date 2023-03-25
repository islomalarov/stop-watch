<template>
  <div class="stopwatchs">
    <StopWatch></StopWatch>
    <StopWatch></StopWatch>
    <StopWatch></StopWatch>
    <StopWatch></StopWatch>
  </div>
</template>

<script>
import StopWatch from './components/StopWatch.vue';

export default {
  name: 'App',
  components: {
    StopWatch
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
