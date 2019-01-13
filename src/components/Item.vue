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
  		title: this.item.data[0].title,
  		desc: this.item.data[0].description,
  		date: this.item.data[0].date_created,
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

		/*@media (min-width: 0px) {
			flex: 0 1 100%;
		}
		@media (min-width: 576px) {
			flex: 0 1 46%;
		}
		@media (min-width: 768px) {
			flex: 0 1 30%;
		}
		@media (min-width: 991px) {
			flex: 0 1 31%;
		}
		@media (min-width: 1059px) {
			flex: 0 1 23%;
		}*/
	}
</style>