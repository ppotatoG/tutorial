<template>
	<div id="app">
		<CopyExample/>
	</div>
</template>

<script>
import CopyExample from './components/CopyExample'

export default {
	name: 'App',
	components: {
		CopyExample
	},
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
}
</style>
