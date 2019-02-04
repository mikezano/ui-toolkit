<template lang="pug">
	Example
		template(slot='title')
			| 1. Show a loader on small actions
		template(slot='good-reason')
			b Good - 
			span The button becomes the loader in this case making it immediately
			| visible what is going on.
		template(slot='bad-reason')
			b Not as good - 
			span Upon clicking nothing happens
		template(slot='good-content')
			form.form
				fieldset 
					legend.form__legend What's your ELF name?
					label.form__label First letter of your name
					input.form__input(
						type="text" 
						name="name" 
						placeholder="A-Z")
					label.form__label Month you were born
					input.form__input(
						type="text"
						name="name"
						placeholder="Jan - Dec")
					.form__footer
						button.simple-button Find out your name!
		template(slot='bad-content')
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/examples/Example.vue';

@Component({
	components: {
		Example,
	},
})
export default class ExampleLoading extends Vue {}
</script>

<style lang="scss" scoped>
@import 'src/toolkit.scss';
@import 'src/variables.scss';
</style>
