<template>
	<div class="rectangle" v-if="showBlock" @click="stopTimer">
		<p class="rectangle__text">click me as fast as u can</p>
	</div>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		}
	},
	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10
			}, 10)
		},
		stopTimer() {
			clearInterval(this.timer)
			this.$emit('end', this.reactionTime)
		}
	},
	mounted() {
		setTimeout(() => {
			this.showBlock = true
			this.startTimer()
		}, this.delay)
	},
}
</script>

<style scoped lang="scss">
	.rectangle {
		width: 500px;
		height: 300px;
		background-color: #14819f;
		border-radius: 20px;
		cursor: pointer;
		&__text {
			font-size: 20px;
			color: #fff;
			text-align: center;
			line-height: 250px;
		}
}
</style>