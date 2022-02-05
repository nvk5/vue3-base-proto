<template>
	<div class="wrapper">
		<div class="wrapper__content">
			<div class="view">
				<div class="container">
					<Form @handleSubmit="handleSubmit"/>
					<TweetList :tweets="items"></TweetList>
				</div>
			</div>
		</div>
  </div>
</template>

<script>
import TweetList from '@/components/List.vue';
import Form from '@/components/Form.vue';

export default {
	components: {
		TweetList,
		Form,
	},
	data() {
		return {
			items: [
				{
					id: 1,
					body: 'Hello Vue3',
					likes: 12,
					avatar: 'https://avatars.dicebear.com/api/male/1.svg',
					date: new Date(Date.now()).toLocaleString(),
				},
				{
					id: 2,
					body: 'Hello World',
					likes: 6,
					avatar: 'https://avatars.dicebear.com/api/male/1.svg',
					date: new Date(Date.now()).toLocaleString(),
				},
			],
		};
	},
	methods: {
		handleSubmit(data) {
			this.items.push(data);
		},
	},
};
</script>
