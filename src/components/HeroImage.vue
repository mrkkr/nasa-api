<template>
  <div class="hero-image">
  </div>
</template>

<script>
export default {
  name: 'HeroImage',
};
</script>

<style lang="scss" scoped>
	.hero-image {
		background-image: url('../assets/heroimage.jpeg');
		background-repeat: no-repeat;
		background-size: cover;
		background-position: center;
		position: fixed;
		top: 0;
		height: 100vh;
		width: 100%;
		z-index: -1;
	}
	.hero-image:after {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		z-index: 1;
		width: 100%;
		height: 100vh;
		background-color: rgba(0,0,0,.4);
	}
</style>
