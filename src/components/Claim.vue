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

		.main-head {
			font-family: 'Audiowide', cursive;
			font-size: 50px;
		}
		.sub-head {
			font-size: 15px;
			margin-top: 15px;
		}
	}
</style>