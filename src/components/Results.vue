<template>
	<div class="results">
		<p class="results__time">Reaction time - {{ score }} ms</p>
		<div class="result__group" v-show="score">
			<h3 class="results__achieve" v-if="score <= 300"> Fast reaction! </h3>
			<h3 class="results__achieve" v-else-if="score > 300 && score < 600"> Good reaction! </h3>
			<h3 class="results__achieve" v-else :class="{ slow: score > 600}"> Slow reaction! </h3>
		</div>
	</div>
</template>

<script>
export default {
	props: ['score'],
}
</script>

<style scoped lang="scss">
	.results {
		display: flex;
		flex-direction: column;
		align-items: center;

		&__time {
			font-size: 18px;
		}

		&__achieve {
			color: #fff;
			background-color: forestgreen;
			padding: 10px 30px 10px 30px;
			font-size: 25px;
		}
}

	.slow {
		background-color: red;
	}
</style>