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
  	<ul>
  		<li v-for="item in results" :key="item.data[0].nasa_id">
  			<img v-bind:src="item.links[0].href" /> 
  		</li>
  	</ul>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Search',
  data() {
  	return {
  		searchValue: '',
  		results: [],
  	};
  },
  methods: {
  	handleInput: debounce(function() {
  		axios.get( `${API}?q=${this.searchValue}&media_type=image` )
  			.then((response) => {
			    // handle success
			  this.results = response.data.collection.items;
			  console.log(this.results);
			})
			.catch((error) => {
			    // handle error
			  console.log(error);
			});
  	}, 500),
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