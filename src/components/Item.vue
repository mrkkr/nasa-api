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
  /* zmienna niżej musi być w computed, bo w obrębie data() byłaby wczytywana zanim kompotent by się w całości wczytał przez co photo byłoby undefined */
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
		width: 300px;
		height: 300px;
	}
</style>