<template>
  <div id="app">
  	<div :class="[{ flexstart: step === 1 }, 'wrapper']">
  		<transition name="slide">
  			<img src='./assets/logo.png' class="logo" v-if="step === 1" />
  		</transition>
  		<transition name="fade">
  			<HeroImage v-if="step === 0" />
  		</transition>
	  	<Claim v-if="step === 0" />
	  	<SearchInput 
	  		v-model="searchValue" 
	  		@input="handleInput" 
	  		v-bind:dark="step === 1" 
	  	/>
	  	<div class="results" v-if="results && !loading && step === 1">
	  		<Item v-for="item in results" v-bind:item="item" v-bind:key="item.data[0].nasa_id" v-on:click.native="handleModalOpen(item)" />
	  	</div>
	  	<div class="loader" v-if="step === 1 && loading"><div></div><div></div></div>
	  	<Modal v-if="modalOpen" v-on:closeModal="modalOpen = false" v-bind:item="modalItem" />
	</div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import HeroImage from '@/components/HeroImage.vue';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Item from '@/components/Item.vue';
import Modal from '@/components/Modal.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'App',
  components: {
  	HeroImage,
  	Claim,
  	SearchInput,
  	Item,
  	Modal
  },
  data() {
  	return {
  		modalOpen: false,
  		modalItem: null,
  		loading: false,
  		step: 0,
  		searchValue: '',
  		results: [],
  	};
  },
  methods: {
  	handleModalOpen(item) {
  		this.modalOpen = true;
  		this.modalItem = item;
  	},
  	handleInput: debounce(function() {
  		this.loading = true;
  		axios.get( `${API}?q=${this.searchValue}&media_type=image` )
  			.then((response) => {
			    // handle success
			  this.results = response.data.collection.items;
			  this.loading = false;
			  this.step = 1;
			})
			.catch((error) => {
			    // handle error
			  console.log(error);
			});
  	}, 500),
  }
};
</script>

<style lang="scss">
	@import url('https://fonts.googleapis.com/css?family=Audiowide&subset=latin-ext');
	@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600');
	
	$font-light: 300;
	$font-normal: 400;
	$font-bold: 600;

	* {
		box-sizing: border-box;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
	body {
		font-family: 'Montserrat', sans-serif;
		font-weight: 300;
		margin: 0;
		padding: 0;
	}
	.fade-enter-active, .fade-leave-active {
	  transition: opacity .3s ease;
	}
	/* środkowych stanów nie zmieniamy, bo mają domyślne wartości */
	.fade-enter, .fade-leave-to {
	  opacity: 0;
	}
	.slide-enter-active, .slide-leave-active {
	  transition: margin-top .3s ease;
	}
	/* środkowych stanów nie zmieniamy, bo mają domyślne wartości */
	.slide-enter, .slide-leave-to {
	  margin-top: -100px;
	}
	.loader {
	  display: inline-block;
	  position: relative;
	  top: 60px;
	  width: 64px;
	  height: 64px;

	  @media (min-width: 768px) {
	  	width: 80px;
	  	height: 80px;
	  }
	}
	.loader div {
	  position: absolute;
	  border: 5px solid #3272ab;
	  opacity: 1;
	  border-radius: 50%;
	  animation: loading 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
	}
	.loader div:nth-child(2) {
	  animation-delay: -0.5s;
	}
	@keyframes loading {
	  0% {
	    top: 28px;
	    left: 28px;
	    width: 0;
	    height: 0;
	    opacity: 1;
	  }
	  100% {
	    top: -1px;
	    left: -1px;
	    width: 58px;
	    height: 58px;
	    opacity: 0;
	  }
	}
	.wrapper {
		position: relative;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		margin: 0;
		padding: 30px;
		width: 100%;
		height: 100vh;

		&.flexstart {
			justify-content: flex-start;
		}
	}
	.logo {
		position: absolute;
		top: 30px;
	}
	.results {
		margin-top: 50px;
		display: flex;
	    flex-wrap: wrap;
	    justify-content: space-around;

	    @media (min-width: 1200px) {
    		max-width: 1140px;
	    }
	}
</style>
