<template>
	<div class="search-wrapper">
  		<input 
  			id="search" 
  			name="search" 
  			v-model="searchValue" 
  			@input="handleInput"
  		/>
  	</div>
</template>

<script>
export default {
  name: 'SearchInput',
};
</script>

<style lang="scss" scoped>
	.search-wrapper {
		display: flex;
		flex-direction: column;
		margin-top: 50px;

		input {
			height: 30px;
			border: 0;
			padding: 5px;
			border-bottom: 1px solid #000;
			background: none;

			&:focus {
				outline: none;
				-webkit-appearance: none;
			    box-shadow: rgba(0,0,0,0.1) 8px 8px 15px 0px;
			    background-color: rgb(255, 255, 255);
			}
		}
	}
</style>