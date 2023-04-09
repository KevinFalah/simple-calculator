<template>
  <div
    class="p-3"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <!-- Result -->
    <div
      class="w-full rounded m-1 p-3 text-end lead fw-bold text-white bg-vue-dark"
    >
      {{ calculatorValue || 0 }}
    </div>

    <!-- Buttons -->
    <div class="row g-0">
      <div class="col-3" v-for="item in calculatorElements" :key="item">
        <div
          class="lead text-center m-1 py-3 bg-vue-dark rounded fw-bold hover-class"
          :class="{
            'bg-vue-green': ['C', '*', '/', '-', '+', '%', '='].includes(item),
          }"
          @click="actionClick(item)"
        >
          {{ item }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="js">
export default {
  name: 'Calculator',
  props: {
      msg: String
  },
  data() {
  return {
      calculatorValue: '',
      calculatorElements: ['C', '*', '/', '-',7,8,9,'+',4,5,6,'%',1,2,3,'=',0,'.'],
      operator: null,
      prevValue: '',
      showPrev: null
  }
},
methods: {
    actionClick(n) {
        if(!isNaN(n) || n === ".") {
            this.calculatorValue += n + ""
        }

        if(n === "C") {
            this.calculatorValue = ""
        }

        if(n === "%") {
            this.calculatorValue = this.calculatorValue / 100 + ""
        }

        if(["+","-","/","*"].includes(n)) {
            this.operator = n
            this.prevValue = this.calculatorValue
            this.calculatorValue = ''
        }

        if(n === "=") {
            this.calculatorValue = eval(
                this.prevValue + this.operator + this.calculatorValue
            )
            this.operator = null
            this.prevValue = ''
        }

    }
}
}
</script>

<style scoped>
.bg-vue-dark {
  background: #31475e;
  color: #ffff;
}
.hover-class:hover {
  cursor: pointer;
  background: #3d5875;
  color: #ffff;
}
.bg-vue-green {
  background: #a5d7e8;
  color: #31475e;
}
</style>
