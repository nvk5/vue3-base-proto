<template>
  <form @submit.prevent="onSubmit" class="form">
    <TextArea
		placeholder="Type tweet here"
		v-model="body"
		required
		class="form__textarea"
    />
    <button type="submit">Submit</button>
  </form>
</template>

<script>
import TextArea from '@/components/UI/TextArea.vue';
import { ref } from 'vue';

export default {
	components: {
		TextArea,
	},
	emits: ['handleSubmit'],

	setup(props, { emit }) {
		const body = ref('');

		const emitData = () => emit('handleSubmit', {
			id: Math.round(Math.random() * 30),
			avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
			body: body.value,
			likes: 0,
			date: new Date(Date.now()).toLocaleString(),
		});

		const onSubmit = () => {
			emitData();
			body.value = '';
		};

		return { body, onSubmit };
	},
};
</script>
<style>
</style>
