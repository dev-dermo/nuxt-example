<template>
	<div>
		<nuxt-link to="/jokes">Back to jokes</nuxt-link>
		<h2>{{ joke }}</h2>
		<hr />
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			joke: {}
		}
	},
	created() {
		axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, {
			headers: {
				'Accept': 'application/json'
			}
		}).then(res => this.joke = res.data.joke)
			.catch(err => console.log(err));
	},
}
</script>