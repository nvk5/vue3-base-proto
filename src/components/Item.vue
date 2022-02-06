<template>
	<li>
		<img :src="tweet.avatar" alt="img" style="width: 30px; height: 30px" />
		<span>{{ tweet.date }}</span>
		<div>{{ tweet.body }}</div>
		<p>likes: {{ tweet.likes }}</p>
	</li>
</template>
<script>
export default {
	props: {
		tweet: {
			type: Object,
			required: true,
		},
	},
};
</script>
<style>
</style>
