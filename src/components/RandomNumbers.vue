<template>
  <div class="numberOuterCont">
    <div
      class="number"
      :id="'number-' + number"
      v-for="number in n()"
      :key="number"
      @mouseover="hov(number)"
      @mouseout="reset"
    >
      {{ number }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      limit: this.$parent.limit,
      numbers: [],
      divArr: [],
    };
  },
  watch: {
    ["$parent.limit"](newLimit) {
      this.limit = newLimit;
    },
  },
  methods: {
    n() {
      let numbers = [];
      for (var i = 0; i <= this.limit; i++) {
        numbers = [...numbers, i];
      }
      return numbers.sort(() => Math.random() - 0.5);
    },
    hov(number) {
      const nums = document.querySelectorAll(".number");
      for (let i = 0; i < nums.length; i++) {
        const num = nums[i].textContent.trim();
        if (number % num === 0) {
          nums[i].classList.add("active");
        }
      }
      document.getElementById("chosenDivisor").innerHTML =
        "Chosen Divisor" + " " + number;
    },
    reset() {
      const nums = document.querySelectorAll(".number");
      nums.forEach((num) => num.classList.remove("active"));
    },
  },
};
</script>

<style scoped>
.numberOuterCont {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;

  width: 100%;
  height: auto;
}

.number {
  display: flex;
  justify-content: center;
  align-items: center;

  width: 2rem;
  height: 2rem;

  cursor: pointer;

  border-radius: 2rem;
  background-color: rgba(211, 211, 211, 0.479);
  opacity: 0.6;
}

.active {
  color: white;
  background-color: red;
  transform: scale(1.2);
  z-index: 999;
  opacity: 1;
  box-shadow: 3px 3px 7px black;
}
</style>
