<template>
	<div>
		<form @submit.prevent="register">
			<label for="email">Email:</label>
			<input v-model="email" type="text" name="email" value />
			<label for="password">Pasword:</label>
			<input v-model="password" type="password" name="password" value />
			<button type="submit" name="button">Login</button>
			<p>{{error}}</p>
			<router-link to="/register">
				Don't have an account? Register
			</router-link>
		</form>
	</div>
</template>


<script>
export default {
	data(){
		return {
			email:"",
			password:"",
			error:null
		}
	},
	methods:{
		register(){
			this.$store.dispatch('login', {
				email:this.email,
				password:this.password
			})
			.then(() =>{
				this.$router.push({name:'dashboard'})
			})
			.catch(err =>{
				console.log(err)
				this.error = err.response.data.error
			})
		}
	}
}

</script>

<style scoped>

</style>