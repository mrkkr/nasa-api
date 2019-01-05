<template>
  <div class="wrapper">
  	<Claim />
  	<SearchInput />
  	<ul>
  		<li v-for="item in results" v-bind:key="item.data[0].nasa_id">
  			<img v-bind:src="item.links[0].href" /> 
  		</li>
  	</ul>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Search',
  components: {
  	Claim,
  	SearchInput,
  },
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
		justify-content: center;
		margin: 0;
		padding: 30px;
		width: 100%;
		height: 100vh;
		background-image: url('../assets/heroimage.jpeg');
		background-repeat: no-repeat;
		background-size: cover;
		background-position: center;
	}
</style>
