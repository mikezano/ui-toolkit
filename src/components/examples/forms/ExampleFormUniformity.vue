<template lang="pug">
	Example
		template(slot='title')
			| 1. Keeping things uniform
		template(slot='good-reason')
			b Good - 
			span inputs are sized the same, creating a nice soothing feel...aaahhh
		template(slot='bad-reason')
			b Bad - 
			span 😨 All types of sizes input appear
		template(slot='good-content')
			form.form
				fieldset 
					legend.form__legend Whats your ELF name?
					label.form__label First Letter of your name
					input.form__input(
						type="text" 
						name="name" 
						placeholder="A-Z"
						v-model="selectedLetter")
					label.form__label Month you were born
					input.form__input(
						type="text"
						name="name"
						placeholder="Jan - Dec"
						v-model="selectedMonth")
					label.form__label Fruit
					select.form__dropdown
						option(selected="selected") Select fruit
						option 🍓 Strawberry
						option 🍍 Pineapple
						option 🥝 Kiwi
					.form__footer
						.default.btn-circle No
						.default.btn-circle(@click='showName') OK
		template(slot='bad-content')
			form.form-bad
				fieldset 
					legend.form__legend Select your handle
					.form__item
						label Name
						input(type="text" name="name" placeholder="Enter Name")
					.form__item
						label Icon
						select
							option(selected="selected") Select option
							option Alpha
							option Beta
							option Charlie
					.form__footer
						.default.btn-circle No
						.default.btn-circle(@click='showName') OK
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

.default {
	@include btn-circle(white, 14px);
}
.form {
	width: 20rem;
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
		display: flex;
		flex-direction: row-reverse;
	}
}

.form-bad {
}
</style>
