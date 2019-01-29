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
					legend.form__legend Person Search

					.form-sections.tabs
						input.tabs__tab#tab1(type="radio" name="tabs" checked)
						label.tabs__label(for="tab1") Basic
						input.tabs__tab#tab2(type="radio" name="tabs")
						label.tabs__label(for="tab2") Location
						input.tabs__tab#tab3(type="radio" name="tabs")
						label.tabs__label(for="tab3") Advanced
						input.tabs__tab#tab4(type="radio" name="tabs")
						label.tabs__label(for="tab4") ???
						.tabs__content
							.content1
								label.form__label First name
								input.form__input(
									type="text"
									name="name"
									placeholder="Enter a first name")
								label.form__label Last Name
								input.form__input(
									type="text"
									name="name"
									placeholder="Enter a last name")
							.content2
								label.form__label Phone Number
								input.form__input(
									type="phone" )
								label.form__label State
								select.form__dropdown
									option(selected="selected") Select state
									option Alaska
									option Arizona
									option California
									option Oregon
									option New York
									option New Jersey
									option Wyoming
									option ...
								label.form__label City
								select.form__dropdown
									option(selected="selected") Select city
									option City 1
									option City 2
									option City 3
									option City 4
									option City 5
									option City 6
									option City 7
									option ...
							.content3
								img(src="https://tinyurl.com/y8n2spmr" width="200" height="200")
							.content4
								label.form__label Fruit
								select.form__dropdown
									option(selected="selected") Select fruit
									option 🍓 Strawberry
									option 🍍 Pineapple
									option 🥝 Kiwi
					.form__footer
						button.simple-button(@click='showName') OK
						button.simple-button No

		template(slot='bad-content')
			form.form
				fieldset 
					legend.form__legend Person Search
					label.form__label First name
					input.form__input(
						type="text"
						name="name"
						placeholder="Enter a first name")
					label.form__label Middle Name
					input.form__input(
						type="text"
						name="name"
						placeholder="Enter a middle name")
					label.form__label Last Name
					input.form__input(
						type="text"
						name="name"
						placeholder="Enter a last name")
					label.form__label Title
					select.form__dropdown
						option(selected="selected") Select title
						option Mr.
						option Mrs.
						option Ms.
					label.form__label Gender
					.form__checkboxes
					
						.checkbox-group
							.checkbox
								input#one.checkbox__button(type='radio' name='test', value='one')
								label.checkbox__label(for='one') Male
							.checkbox
								input#two.checkbox__button(type='radio' name='test', value='two')
								label.checkbox__label(for='two') Female

					label.form__label Age Range
					.form__checkboxes
						.checkbox-group
							.checkbox
								input#young.checkbox__button(type='radio' name='age-range', value='one')
								label.checkbox__label(for='young') 0 - 25
							.checkbox
								input#middle.checkbox__button(type='radio' name='age-range', value='two')
								label.checkbox__label(for='middle') 26 - 50
							.checkbox
								input#old.checkbox__button(type='radio' name='age-range', value='three')
								label.checkbox__label(for='old') 50 +
					label.form__label Date of Birth
					input.form__input(
						type="date" 
						placeholder="Birthdate")
					label.form__label Phone Number
					input.form__input(
						type="phone" )
					label.form__label State
					select.form__dropdown
						option(selected="selected") Select state
						option Alaska
						option Arizona
						option California
						option Oregon
						option New York
						option New Jersey
						option Wyoming
						option ...
					label.form__label City
					select.form__dropdown
						option(selected="selected") Select city
						option City 1
						option City 2
						option City 3
						option City 4
						option City 5
						option City 6
						option City 7
						option ...
					label.form__label Vetran?
					.form__checkboxes
						.checkbox-group
							.checkbox
								input#no-vetran.checkbox__button(type='radio' name='vetran', value='one')
								label.checkbox__label(for='no-vetran') No
							.checkbox
								input#yes-vetran.checkbox__button(type='radio' name='vetran', value='two')
								label.checkbox__label(for='yes-vetran') Yes
					.form__footer
						button.simple-button(@click='showName') OK
						button.simple-button No
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/examples/Example.vue';

interface Hash {
	[s: string]: string;
}

@Component({
	components: {
		Example,
	},
})
export default class ExampleFormExcessFields extends Vue {
	public letterToName: Hash = {};
	public monthToName: Hash = {};
	private selectedLetter: string = '';
	private selectedMonth: string = '';
	private selectedFruit: string = '';

	public mounted() {
		this.letterToName['A'] = 'Perky';
		this.letterToName['B'] = 'Nipper';
		this.letterToName['C'] = 'Bubbles';
		this.letterToName['D'] = 'Happy';

		this.monthToName['Jan'] = 'Angel-Pants';
		this.monthToName['Feb'] = 'Floppy-Feet';
		this.monthToName['Mar'] = 'Plum-Pants';
	}

	public showName() {
		console.log(this.selectedLetter);
		console.log(this.letterToName['A']);
		alert(this.selectedLetter);
		const finalName = `${this.letterToName[this.selectedLetter]} ${
			this.monthToName[this.selectedMonth]
		}`;
		console.log(finalName);
	}
}
</script>

<style lang="scss" scoped>
@import 'src/toolkit.scss';
@import 'src/variables.scss';

.default {
	@include btn-circle(white, 14px);
}

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
		font-size: 1rem;
	}
	&__checkboxes {
		margin: 0.2rem auto 0.6rem;
		@include checkbox-group(1);
	}
	&__footer {
		display: flex;
		button {
			@include simpleButton();
		}
		button:first-child {
			margin-left: 0;
		}
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

.form-sections {
	@include underlined_tabs(4);
}
</style>
