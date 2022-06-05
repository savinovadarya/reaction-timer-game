<template>
	<div class="main">
		<h1 class="main__title">Let's test your reaction</h1>
		<button class="main__btn" @click="showRectangle" :class="{ btnBg: isBtnClick }">play</button>
		<Rectangle v-if="isShownRectangle" :delay="delay" @end="endGame"/>
		<Results :score="score" v-if="score"/>
	</div>
	</template>
<script>
import Rectangle from './components/Rectangle.vue'
import Results from './components/Results.vue'

export default {
	components: {
		Rectangle,
		Results,
	},
	data() {
		return {
			isShownRectangle: false,
			delay: null,
			isBtnClick: false,
			score: null,
		}
	},
	methods: {
		showRectangle() {
			this.score = null
			this.isBtnClick = !this.isBtnClick
			this.delay = 1000 + Math.random() * 5000
			this.isShownRectangle = !this.isShownRectangle
		},
		endGame(reactionTime) {
			this.score = reactionTime
			this.isShownRectangle = !this.isShownRectangle
			this.isBtnClick = !this.isBtnClick
		}
	},
}
</script>

<style scoped lang="scss">
	.main {
		display: flex;
		flex-direction: column;
		align-items: center;

		&__btn {
			padding: 10px 40px 10px 40px;
			color: #fff;
			background-color: #091940;
			border-radius: 10px;
			border: 0;
			cursor: pointer;
			margin: 0px 0px 50px 0px;
		}
	}
	.btnBg {
		background-color: #3d4e7b;
		cursor: default;
	}
</style>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
* {
	font-family: 'Roboto', sans-serif;
}
</style>