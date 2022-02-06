<template>
	<select v-model="sortBy">
		<option	v-for="method of sortMethod" :key="method">
			{{ method }}
		</option>
	</select>
	<ul>
		<Item v-for="tweet in sorteredItems" :key="tweet.id" :tweet="tweet" />
	</ul>
</template>
<script>
import Item from '@/components/Item.vue';
import { computed, ref } from 'vue';

export default {
	components: { Item },
	props: {
		tweets: {
			type: Array,
			required: true,
		},
	},
	setup(props) {
		const sortBy = ref('date');
		const sortMethod = ['date', 'likes'];

		/*
			Чтобы eslint не ругался на изменение пропсов (пропсы в дочернем компоненте изменять нельзя)
			создадим отдельный метод и его прокинем в computed/
			As my above comment, you should not edit other data in computed property,
			you should use watch instead
		*/
		const sorting = (sortData) => sortData.sort((a, b) => {
			if (a[sortBy.value] > b[sortBy.value]) return 1;
			if (a[sortBy.value] < b[sortBy.value]) return -1;
			return 0;
		});

		// проходимся v-for уже по отсортированому массиву
		const sorteredItems = computed(() => sorting(props.tweets));

		return { sortBy, sortMethod, sorteredItems };
	},
};
</script>
<style >
</style>
