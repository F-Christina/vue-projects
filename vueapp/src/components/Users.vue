<template>
	<div class="users">
		<h1>users</h1>

		<!-- 添加用户信息 -->
		<form v-on:submit="addUser">
			<input type="text" v-model="newUser.name" placeholder="Enter name">
			<input type="text" v-model="newUser.email" placeholder="Enter email">
			<input type="submit" value="Submit">
		</form>


		<!-- 展示用户信息 -->
		<ul>
			<li v-for="user in users">
				<input type="checkbox" class="toggle" v-model="user.contacted">
				<span :class="{contacted:user.contacted}">
					{{user.name}} : {{user.email}}
					<button v-on:click="deleteUser(user)">x</button>
			</span>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: "users",
		data(){
			return{
				newUser:{},
				users:[
					{
						name:"Hemia",
						email:"hemia@gmail.com",
						contacted:false
					},
					{
						name:"Henry",
						email:"henry@gmail.com",
						contacted:false
					},
					{
						name:"Emily",
						email:"emily@gmail.com",
						contacted:false
					}
				]
			}
		},
		methods:{
			addUser:function (e){
				//console.log("sasdasdas")
				this.users.push({
					name:this.newUser.name,
					email:this.newUser.email,
					contacted:false
				})
				e.preventDefault();
			},
			deleteUser:function (user){
				// console.log("sasdasdas")
				this.users.splice(this.users.indexOf(user),1)
			}
		},
		created:function (){
			//console.log("hello")
			this.$http.get("http://jsonplaceholder.typicode.com/users")
			.then(function (response){
				//console.log(response)t
				this.users = response.data;

			})
		}
	}
</script>

<style scoped>
	.contacted{
		text-decoration: line-through;
	}
</style>