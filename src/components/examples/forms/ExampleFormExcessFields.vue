<template lang="pug">
	Example
		template(slot='title')
			| 2. Reducing amount of fields
		template(slot='good-reason')
			b Good - 
			span Lots of possibilities, seperate them into different tabs
			| placing the less important ones on the secondary tabs
		template(slot='bad-reason')
			b Not as good - 
			span Do you really need that many optiosn to search by
			| A smorgasbord of fields lacking rythm in balance leaving 
			| the user confused as to what should be filled in.
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
					label.form__label Is round?
					.form__checkboxes
					
						.checkbox-group
							.checkbox
								input#one.checkbox__button(type='radio' name='test', value='one')
								label.checkbox__label(for='one') One
							.checkbox
								input#two.checkbox__button(type='radio' name='test', value='two')
								label.checkbox__label(for='two') Two
							.checkbox
								input#three.checkbox__button(type='radio' name='test', value='three')
								label.checkbox__label(for='three') Three
					label.form__label Is color
					.form__checkboxes
					
						.checkbox-group
							.checkbox
								input#one.checkbox__button(type='radio' name='test', value='one')
								label.checkbox__label(for='one') One
							.checkbox
								input#two.checkbox__button(type='radio' name='test', value='two')
								label.checkbox__label(for='two') Two
							.checkbox
								input#three.checkbox__button(type='radio' name='test', value='three')
								label.checkbox__label(for='three') Three
					label.form__label Primary title
					input.form__input(
						type="text" 
						name="name" 
						placeholder="A-Z"
						v-model="selectedLetter")
					label.form__label Secondary title
					input.form__input(
						type="text"
						name="name"
						placeholder="Jan - Dec"
						v-model="selectedMonth")

					.form__footer
						.default.btn-circle No
						.default.btn-circle(@click='showName') OK

					//.container
						input#tab1(type="radio" name="tabs" checked)
						label(for="tab1") Tab 1
						input#tab2(type="radio" name="tabs")
						label(for="tab2") Tab 2
						input#tab3(type="radio" name="tabs")
						label(for="tab3") Tab 3
						input#tab4(type="radio" name="tabs")
						label(for="tab4") Tab 4
						.content
							.content1
							.content2
								| Content for Tab 2
							.content3
								img(src="https://tinyurl.com/y8n2spmr" width="200" height="200")
							.content4
								| Content for Tab 4
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
export default class ExampleFormExcessFields extends Vue {
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
//@include underlined_tabs();
.form {
	//width: 20rem;
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
		display: block;
	}
	&__checkboxes {
		margin: 0.2rem auto 0.6rem;
		@include checkbox-group(1);
	}
	&__footer {
		display: flex;
		flex-direction: row-reverse;
	}
}

.form-bad {
	&__item {
		display: block;
	}
	input,
	select {
		width: 80%;
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
