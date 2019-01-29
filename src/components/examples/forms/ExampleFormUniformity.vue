<template lang="pug">
	Example
		template(slot='title')
			| 1. Keep things uniform
		template(slot='good-reason')
			b Good - 
			span inputs are sized the same, creating a nice Feng Shui feel...aaahhh
		template(slot='bad-reason')
			b Not as good - 
			span Different alignments between the header text and 
			| the form contents, spacing is off,creating a jagged, unpolished look 😨.
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
			form.form-bad
				fieldset 
					legend.form__legend What's your ELF name ?
					.form__item
						label First letter of your name
						input(type="text" name="name" placeholder="A-Z")
					.form__item
						label Month you were born
						input(
							type="text"
							name="name"
							placeholder="Jan - Dec")
					.form__footer
						button.simple-button Find out your name!
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Example from "@/components/examples/Example.vue";

interface Hash {
	[s: string]: string;
}

@Component({
	components: {
		Example
	}
})
export default class ExampleFormUniformity extends Vue {
	public letterToName: Hash = {};
	public monthToName: Hash = {};
	private selectedLetter: string = "";
	private selectedMonth: string = "";
	private selectedFruit: string = "";

	public mounted() {
		this.letterToName["A"] = "Perky";
		this.letterToName["B"] = "Nipper";
		this.letterToName["C"] = "Bubbles";
		this.letterToName["D"] = "Happy";

		this.monthToName["Jan"] = "Angel-Pants";
		this.monthToName["Feb"] = "Floppy-Feet";
		this.monthToName["Mar"] = "Plum-Pants";
	}

	public showName() {
		console.log(this.selectedLetter);
		console.log(this.letterToName["A"]);
		alert(this.selectedLetter);
		const finalName = `${this.letterToName[this.selectedLetter]} ${
			this.monthToName[this.selectedMonth]
		}`;
		console.log(finalName);
	}
}
</script>

<style lang="scss" scoped>
@import "src/toolkit.scss";
@import "src/variables.scss";

.form {
	fieldset {
		background-image: linear-gradient(transparent, lighten(#17a2b8, 50%));
	}
	fieldset {
		padding: 1rem;
		text-align: left;
	}
	&__legend {
		font-weight: bold;
	}
	&__input,
	&__dropdown {
		display: block;
		width: 100%;
		padding: 0.3rem;
		margin: 0.2rem auto 0.6rem; //top left&right bottom
		border: 0.1rem solid $mainD1;
		box-sizing: border-box;
	}
	&__label {
		padding: 0;
		margin: 0;
	}
	&__footer {
		margin-left: 0rem;
		button {
			@include simpleButton();
			&.simple-button {
				margin-left: 0;
			}
		}
	}
}

.form-bad {
	fieldset {
		background-image: linear-gradient(transparent, lighten(#dc3545, 40%));
	}
	&__item {
		display: block;
	}
	input,
	select {
		padding: 0.3rem;
		margin: 0.8rem auto;
		border: 0.1rem solid $mainD1;
		box-sizing: border-box;
	}
	&__footer {
		display: flex;
		flex-direction: row-reverse;
	}
}
</style>
