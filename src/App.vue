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
import { ref } from 'vue';

export default {
	components: {
		TweetList,
		Form,
	},

	setup() {
		const items = ref([
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
		]);

		const handleSubmit = (item) => items.value.push(item);

		return { items, handleSubmit };
	},
};
</script>
