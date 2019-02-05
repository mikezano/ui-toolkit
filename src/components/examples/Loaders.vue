<template lang="pug">
	.home
		h1 Loaders
		.message(style="text-align:left;")
			| Indicating that 'something' is happening tends to be a problem in that its not
			| always obvious that you are waiting because nothing conveys the issue.
		
		ExampleLoading
		ExampleLoadingArea
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import ExampleLoading from '@/components/examples/loading/ExampleLoading.vue';
import ExampleLoadingArea from '@/components/examples/loading/ExampleLoadingArea.vue';

@Component({
	components: {
		ExampleLoading,
		ExampleLoadingArea,
	},
})
export default class Loaders extends Vue {}
</script>

<style lang="scss" scoped>
.home {
	display: flex;
	flex-direction: column;
	align-items: center;
}
.message {
	width: 50rem;
}
</style>
