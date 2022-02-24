<template>
  <Card />
</template>

<script>
import Card from './components/Card.vue';
export default {
  components: {
    Card,
  }
}
</script>

<style>
:root {
  --clr-lightCyan: hsl(193, 38%, 86%);
  --clr-neonGreen: hsl(150, 100%, 66%);

  --bg-grayishBlue: hsl(217, 19%, 38%);
  --bg-darkGrayishBlue: hsl(217, 19%, 24%);

  --ft-family: 'Manrope', sans-serif;
}

body {
  font-family: var(--ft-family);
  font-weight: 300;

  background-color: var(--bg-grayishBlue);
}
</style>