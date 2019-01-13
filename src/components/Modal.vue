<template>
	<div class="modal-wrapper">
		<div class="inner-wrapper">
			<div class="photo">

			</div>
			<div class="description">
				<h2 class="title"></h2>
				<p class="description">
				</p>
			</div>
		</div>
		<div class="close" v-on:click="$emit('closeModal')"></div>
	</div>
</template>

<script>
export default {
  name: 'Modal',
};
</script>

<style lang="scss" scoped>
	.modal-wrapper {
		max-width: 100%;
		position: fixed;
		top: 0;
		left: 0;
		background-color: #f6f6f6;

		.inner-wrapper {
			display: flex;
			justify-content: center;
			align-items: center;
			flex-direction: column;
			height: 100%;
			padding: 50px;

			.photo {
				width: 100%;
				height: auto;
				background: #000;

				img {
					width: 100%;
				}
			}
			.description {
				color: #333;
			}
		}
		.close {
			position: absolute;
			width: 30px;
			height: 30px;
			padding: 30px;
			right: 0;
			left:  0;
			cursor: pointer;

			&::before,
			&::after {
				position: absolute;
				top: 30px;
				right: 20px;
				content: '';
				width: 20px;
				height: 2px;
				background: #000;
				display: block;
			}
			&::before {
				transform: rotate(45deg);
			}
			&::after {
				transform: rotate(-45deg);
			}
		}
	}
</style>