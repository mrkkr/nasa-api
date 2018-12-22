<template>
  <div class="wrapper">
  	<div class="search">
  		<label for="search">Search</label>
  		<input 
  			id="search" 
  			name="search" 
  			v-model="searchValue" 
  			@input="handleInput"
  		/>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'Search',
  data() {
  	return {
  		searchValue: '',
  	};
  },
  methods: {
  	handleInput() {
  		console.log(this.searchValue);
  	},
  }
};
</script>

<style lang="scss" scoped>
	.wrapper {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin: 0;
		padding: 30px;
		width: 100%;
	}
	.search {
		display: flex;
		flex-direction: column;
		max-width: 300px;

		label {
			font-family: 'Montserrat', sans-serif;
		}
		input {
			height: 30px;
			border: 0;
			padding: 5px;
			border-bottom: 1px solid #000;

			&:focus {
				outline: none;
				-webkit-appearance: none;
			    box-shadow: rgba(0,0,0,0.1) 8px 8px 15px 0px;
			    background-color: rgb(255, 255, 255);
			}
		}
	}
</style>