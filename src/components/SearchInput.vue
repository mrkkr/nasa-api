<template>
	<div class="search-wrapper">
  		<input 
  			id="search" 
  			name="search"
  			v-bind:class="{ dark: dark }"
  			v-bind:value="value"
  			v-on:input="handleChange"
  		/>
  	</div>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
  	value: {
  		type: String,
  		required: true,
  	},
  	dark: {
  		type: Boolean,
  		default: false,
  	},
  },
  methods: {
  	handleChange(e) {
  		this.$emit('input', e.target.value);
  	}
  }
};
</script>

<style lang="scss" scoped>
	.search-wrapper {
		display: flex;
		flex-direction: column;
		margin-top: 100px;

		input {
			height: 30px;
			border: 0;
			color: #fff;
			font-family: 'Montserrat', sans-serif;
			font-size: 16px;
			text-align: center;
			padding: 5px;
			border-bottom: 1px solid #fff;
			background: none;
			transition: box-shadow .5s ease-out;

			@media (min-width: 991px) {
				font-weight: 400;
			}

			&:focus {
				outline: none;
				-webkit-appearance: none;
			    box-shadow: rgba(255,255,255,0.5) 0 10px 20px -8px;
			    background-color: transparent;
			}
		}
		.dark {
			color: #1e3d4a;
			border-bottom: 1px solid #1e3d4a;

			&:focus {
				outline: none;
				-webkit-appearance: none;
			    box-shadow: rgba(#1e3d4a,0.5) 0 10px 20px -8px;
			    background-color: transparent;
			}
		}
	}
</style>