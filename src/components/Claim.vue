<template>
	<div class="claim-wrapper">
		<h1 class="main-head">Spacewalk</h1>
		<p class="sub-head">
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam.
		</p>
		<p class="sub-head">
			Quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
		</p>
	</div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>
	.claim-wrapper {
		text-align: center;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		color: #fff;

		.main-head {
			font-family: 'Audiowide', cursive;
			font-size: 53px;
			margin: 0;

			@media (min-width: 768px) {
				font-size: 80px;
			}
			@media (min-width: 991px) {
				font-size: 100px;
			}
		}
		.sub-head {
			font-size: 15px;
			margin-top: 20px;
			max-width: 500px;

			@media (min-width: 768px) {
				font-size: 18px;
				letter-spacing: 1px;
				line-height: 1;
			}
			@media (min-width: 991px) {
				line-height: 1.2;
			}
		}
	}
</style>