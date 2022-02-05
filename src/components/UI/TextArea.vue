<template>
	<textarea
		:required="required"
		:placeholder="placeholder"
		@input="$emit('update:modelValue', $event.target.value)"
		:value="modelValue"
		class="textarea"
	/>
</template>
<script>
export default {
	props: {
		modelValue: {
			type: String,
		},
		placeholder: {
			type: String,
		},
		required: {
			type: [Boolean],
		},
	},
};
</script>
<style>
</style>
