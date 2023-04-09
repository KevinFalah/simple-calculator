<template>
  <div
    id="app"
    class="d-flex justify-content-center flex-column align-items-center"
    style="height: 100vh"
  >
    <h1 class="text-center text-light">Calculator</h1>
    <Calculator></Calculator>
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";
export default {
  name: "App",
  components: {
    Calculator,
  },
};
</script>
