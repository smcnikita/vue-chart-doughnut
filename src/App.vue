<script setup>
import ChartDoughnut from './components/ChartDoughnut.vue';
</script>

<template>
  <div class="wrapper">
    <chart-doughnut
      class="p-3"
      per="5"
      color="#C3AED6"
      color-bg="#CDC9C3"
      text-size="40"
    />
    <chart-doughnut class="p-3" per="85" />
    <chart-doughnut class="p-3" per="100" />
  </div>
</template>

<style>
.wrapper {
  display: flex;
}

.p-3 {
  padding: 1rem;
}
</style>
