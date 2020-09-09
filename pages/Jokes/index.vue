<template>
	<div>
		Jokes

		<Joke
			v-for="joke in jokes"
			v-bind:key="joke.id"
			v-bind:id="joke.id"
			v-bind:joke="joke.joke"
		/>
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			jokes: []
		};
	},

	created() {
		axios.get('https://icanhazdadjoke.com/search', {
			headers: {
				'Accept': 'application/json'
			}
		}).then(res => this.jokes = res.data.results)
			.catch(err => console.log(err));
	},

	head() {
		return {
			title: 'Dad Jokes',
			meta: [
				{
					hid: 'description',
					name: 'description',
					content: 'Best place for corney Dad joesk!'
				}
			]
		};
	}
}
</script>