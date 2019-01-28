<template>
	<div v-bind:style="style" class="grid-item"></div>
</template>

<script>
export default {
  name: 'Item',
  props: {
  	item : {
  		type: Object,
  		required: true,
  	},
  },
  data() {
  	return {
  		photo: this.item.links[0].href,
  	};
  },
  /* zmienna niżej musi być w computed, bo w obrębie data() byłaby wczytywana zanim komponent by się w całości wczytał przez co zmienna photo byłaby undefined */
  computed: {
  	style() {
  		return `background-image: url("${this.photo}")`;
  	}
  }
};
</script>

<style lang="scss" scoped>
	.grid-item {
		background-size: cover;
		background-repeat: no-repeat;
		background-position: center;
		height: 250px;
		min-width: 250px;
		flex-grow: 1;
		margin: 10px;

		&:hover {
			cursor: pointer;
		}
	}
</style>