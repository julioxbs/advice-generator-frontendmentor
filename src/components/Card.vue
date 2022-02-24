<template>
  <div class="container vh-100 d-flex align-items-center justify-content-center p-2">
      <div class="box-quote w-100 text-center rounded-3 p-5 position-relative shadow">
          <p>Advice #{{id}}</p>

          <h1>{{text}}</h1>

          <div class="line my-4">
              <span class="icon d-flex justify-content-center">
                <img class="d-block d-md-none" src="/images/pattern-divider-mobile.svg" alt="icon">
                <img class="d-none d-md-block" src="/images/pattern-divider-mobile.svg" alt="icon">
              </span>
          </div>

          <div class="bg-dice position-absolute icon-dice" @click="generatorDevice">
              <img src="/images/icon-dice.svg" alt="dice">
          </div>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            id: 0,
            text: '',
        }
    },

    methods: {
        async generatorDevice() {
            try {
                let res = await fetch('https://api.adviceslip.com/advice')
                let data = await res.json()
                let {id, advice} = data.slip
                this.id = id, this.text = advice
            } catch (error) {
                console.log(error)
            }
        }
    },

    mounted() {
        this.generatorDevice()
    }
}
</script>

<style>
.box-quote {
    background-color: var(--bg-darkGrayishBlue);
    max-width: 500px;
}

.box-quote p {
    color: var(--clr-neonGreen);
    font-size: 18px;
}

.box-quote h1 {
    color: var(--clr-lightCyan);
    font-weight: bold;
    font-size: 28px;
}

.icon-dice {
    bottom: 0;
    left: 50%;
    transform: translate(-50%, 50%);
}

.bg-dice {
    background-color: var(--clr-lightCyan);
    display: flex;
    align-items: center;
    justify-content: center;

    width: 50px;
    height: 50px;
    border-radius: 50%;
    transition: all .3s;
}

.bg-dice:hover {
    background-color: var(--clr-neonGreen);
    box-shadow: 0 0 0 1px var(--clr-neonGreen);
    cursor: pointer;
}
</style>