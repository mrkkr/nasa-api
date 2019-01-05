<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
	@import url('https://fonts.googleapis.com/css?family=Audiowide&subset=latin-ext');
	@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600');
	
	$font-light: 300;
	$font-normal: 400;
	$font-bold: 600;

	* {
		box-sizing: border-box;
	}
	body {
		font-family: 'Montserrat', sans-serif;
		margin: 0;
		padding: 0;
	}
</style>
