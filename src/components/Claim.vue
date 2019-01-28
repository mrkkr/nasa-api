<template>
	<div class="claim-wrapper">
		<h1 class="main-head">Spacewalk</h1>
		<p class="sub-head">
			Simple application that allows you to find anything about space from the NASA databases.
		</p>
		<p class="sub-head">
			Type something in search input and explore the space yourself!
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