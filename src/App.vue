<template>
  <div id="app">
    <div class="appInner">
      <div class="appHeaderText">
        <h1 class="appHeader">Divisors</h1>
        <p class="appHeaderSubText">
          Hover over any number and it's divisible numbers will be higlighted.
        </p>
      </div>
      <input
        id="numInput"
        type="number"
        max="100"
        v-model="limit"
        @input="updateValue"
      />
      <Numbers />
      <div id="chosenDivisor">Chosen Divisor:</div>
    </div>
  </div>
</template>

<script>
import Numbers from "./components/RandomNumbers.vue";

export default {
  name: "App",
  components: {
    Numbers,
  },
  data() {
    return {
      limit: 100,
    };
  },
  methods: {
    updateValue(event) {
      const value = event.target.value;
      console.log(value, this.limit);
      if (String(value).length <= 3) {
        this.limit = value;
      }
      this.$forceUpdate();
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  display: flex;
  justify-content: center;
  align-content: center;
  gap: 1rem;

  width: 100vw;
  height: 100vh;
  background-color: rgb(41, 41, 41);
}
.appInner {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 2rem;

  width: 50vw;
  height: auto;
}
.appHeaderText {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 1rem;
}
.appHeader {
  font-size: 3rem;
  color: white;
  text-transform: uppercase;
}
.appHeaderSubText {
  font-size: 1.2rem;
  color: white;
}
#numInput {
  width: auto;
  height: 1.5rem;

  color: white;
  background-color: rgba(255, 255, 255, 0);
  border: none;
  border-bottom: 1px solid rgba(163, 162, 162, 0.747);

  padding: 1rem;
  font-size: 1.2rem;
}
#numInput:focus {
  outline: none;
  border-bottom: 1px solid rgb(255, 255, 255);
}
#chosenDivisor {
  font-size: 2rem;
  color: white;
  text-transform: uppercase;
}
</style>
