<template lang="pug">
	Example
		template(slot='title')
			| 1. Show an unobtrusive loader for actions
		template(slot='good-reason')
			b Good - 
			span The button here has a loader indicator next to the input 
			| which immediately appears and would remain until the action completes.
		template(slot='bad-reason')
			b Not as good - 
			span Upon clicking nothing happens
		template(slot='good-content')
			form#example.simple-form(v-on:submit.prevent)
				fieldset.simple-form__fieldset
					legend.simple-form__legend Search for something
					label.simple-form__label Search Term
					input.simple-form__input(
						type="text" 
						name="name" 
						placeholder="Enter anything you can think of!")
					.simple-form__footer
						button(@click="toggleLoader()").simple-button Find that thing!
						div(v-if="isLoading")
							span.simple-spin 🔎
							span Searching...
		template(slot='bad-content')
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Example from "@/components/examples/Example.vue";

@Component({
	components: {
		Example
	}
})
export default class ExampleLoading extends Vue {
	private isLoading: boolean = false;

	public toggleLoader(): void {
		this.isLoading = !this.isLoading;
		setTimeout(() => {
			this.isLoading = false;
		}, 3000);
	}
}
</script>

<style lang="scss" scoped>
@import "src/toolkit.scss";
@import "src/variables.scss";

#example {
	@include simple-form();
}

.simple-spin {
	animation: simple-spin 1s linear infinite;
	font-size: 1.8rem;
}
@keyframes simple-spin {
	from {
		transform: rotateY(0);
	}
	to {
		transform: rotateY(360deg);
	}
}
</style>
