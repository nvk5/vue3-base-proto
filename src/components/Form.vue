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

export default {
	components: {
		TextArea,
	},
	data() {
		return {
			body: '',
		};
	},
	methods: {
		onSubmit() {
			this.$emit('handleSubmit', {
				id: Math.round(Math.random() * 30),
				avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
				body: this.body,
				likes: 0,
				date: new Date(Date.now()).toLocaleString(),
			});

			this.body = '';
		},
	},
};
</script>
<style>
</style>
