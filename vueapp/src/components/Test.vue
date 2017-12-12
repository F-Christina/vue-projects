<template>
	<div class="test">
		<h1>{{title}}</h1>
		<p>{{user.firstName}}</p>
		<p v-text="user.lastName"></p>
	</div>
</template>

<script>
	export default {
		name: "test",
		data(){
			return{
				title:"Hello Vue.js!",
				user:{
					firstName:"Hemiah",
					lastName:"Wu"
				}
			}
		}
	}
</script>

<style scoped>
	
</style>