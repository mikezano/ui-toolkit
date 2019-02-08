<template lang="pug">
	Example
		template(slot='title')
			| 3. Adding buttons to Dialogs
		template(slot='good-reason')
			b Good - 
			span Labels on the left aligned for easy visual scanning
		template(slot='bad-reason')
			b Bad - 
			span Labels next to each other, adds extra width
		template(slot='good-content')
			div.panel
				.panel__header Confirmation
				.panel__body
					| Are you sure ?
				.panel__footer
					.default.btn-circle No
					.default.btn-circle OK
		template(slot='bad-content')
			div.panel
				.panel__header Confirmation
				.panel__body
					| Are you sure ?
				.panel__footer
					.default.btn-circle No
					.default.btn-circle OK
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/examples/Example.vue';

@Component({
	components: {
		Example,
	},
})
export default class ExampleButtonDialog extends Vue {}
</script>

<style lang="scss" scoped>
@import 'src/toolkit.scss';
@import 'src/variables.scss';

.default {
	@include btn-circle(white, 14px);
}
.panel {
	width: 20rem;
	border: 1px solid $main;
	&__header,
	&__body,
	&__footer {
		padding: 1rem;
	}
	&__header {
		background-image: linear-gradient($main, $mainL1);
	}
	&__body {
		padding-bottom: 0;
	}
	&__footer {
		display: flex;
		flex-direction: row-reverse;
		padding-top: 0;
	}
}
</style>
