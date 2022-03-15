<script setup>
import ChartDoughnut from './components/ChartDoughnut.vue';
</script>

<template>
	<div class="wrapper">
		<ChartDoughnut class="p-3" per="5" color="#C3AED6" color-bg="#CDC9C3" text-size="40" />
		<ChartDoughnut class="p-3" per="85" />
		<ChartDoughnut class="p-3" per="100" />
	</div>
</template>

<style lang="scss">
.wrapper {
	display: flex;
}

.p-3 {
	padding: 1rem;
}
</style>
