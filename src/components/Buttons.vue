<template lang="pug">
	.home
		.message
			| Buttons are used and abused.  I see them misplaced randomly and not
			| consistently
		
		.example
			.example__good-reason
				b Good - 
				span First column showing the actionable items so you know what you can do
			.example__bad-reason
				b Bad - 
				| Action items are located in the middle of the table, we read left to right, put them in the front
			.example__good-content
				table.table
					thead
						tr
							th Action
							th City
							th State
							th Country
					tbody
						tr.table__row
							td
								.default.btn-circle 🍓
							td Scottsdale
							td AZ
							td U.S.A
						tr.table__row
							td
								.default.btn-circle 🍓
							td Scottsdale
							td AZ
							td Pakistan
						tr.table__row
							td
								.default.btn-circle 🍓
							td Scottsdale
							td AZ
							td China
						tr.table__row
							td
								.default.btn-circle 🍓
							td Scottsdale
							td AZ
							td Japan
			.example__bad-content
				table.table
					thead
						tr
							th State
							th City
							th Action
							th Country
					tbody
						tr.table__row
							td Scottsdale
							td AZ
							td
								.default.btn-circle 🍓
							td U.S.A
						tr.table__row
							td Scottsdale
							td AZ
							td
								.default.btn-circle 🍓
							td Pakistan
						tr.table__row
							td Scottsdale
							td AZ
							td
								.default.btn-circle 🍓
							td China
						tr.table__row
							td Scottsdale
							td AZ
							td
								.default.btn-circle 🍓
							td Japan

		.example
			.example__good-reason
				b Good - 
				span Labels on the left aligned for easy visual scanning
			.example__bad-reason
				b Bad - 
				span Labels next to each other, adds extra width
			.example__good-content
				form.form
					fieldset 
						legend Select your handle
						label Name
						input.form__input(type="text" name="name" placeholder="Enter Name")
						label Icon
						select.form__dropdown
							option(selected="selected") Select option
							option Alpha
							option Beta
							option Charlie
						.form__footer
							.default.btn-circle No
							.default.btn-circle OK
			.example__bad-content
				form.form-bad
					fieldset 
						legend Select your handle
						.form-bad__item
							label Name
							input(type="text" name="name" placeholder="Enter Name")
						.form-bad__item
							label Icon
							select
								option(selected="selected") Select option
								option Alpha
								option Beta
								option Charlie
						.form-bad__footer
							.default.btn-circle No
							.default.btn-circle OK

		ExampleButtonDialog
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/Example.vue';
import ExampleButtonDialog from '@/components/ExampleButtonDialog.vue';

@Component({
	components: {
		Example,
		ExampleButtonDialog,
	},
})
export default class Buttons extends Vue {}
</script>

<style lang="scss" scoped>
@import 'src/toolkit.scss';
$main: hsla(0, 0, 80%, 1);
$mainL1: lighten($main, 10%);
$mainD1: darken($main, 10%);

body {
	display: flex;
	align-items: center;
	justify-content: center;
}
.home {
	//width: 60rem;

	display: flex;
	flex-direction: column;
	//justify-content: center;
	align-items: center;
}
.default {
	@include btn-circle(white, 14px);
}
.example {
	width: 52rem;
	//border: 1px solid $main;
	padding: 2rem;
	display: grid;
	//grid-template-rows: 50% 50%;
	grid-template-columns: 50% 50%;

	justify-content: space-between;
	align-items: center;

	//padding: 0.5rem;
	//border: 0.1rem solid;
	//justify-content: space-around;

	&__title {
		grid-row: 1;
		grid-column: 1/3;
		font-weight: bold;
		font-size: 2rem;
		text-align: left;
	}
	&__good-reason,
	&__good-content,
	&__bad-reason,
	&__bad-content {
		padding: 0.5rem;
	}
	&__good-reason,
	&__bad-reason {
		text-align: left;
	}
	&__bad {
	}
}
.table {
	border-collapse: collapse;
	&__row:hover {
		background-color: whitesmoke;
	}
	th {
		background-image: linear-gradient($main, $mainL1);
	}
	td,
	th {
		border-bottom: 0.1rem solid lightgray;
		padding: 0.2rem 1rem;
	}
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

.form {
	width: 20rem;
	fieldset {
		padding: 1rem;
		text-align: left;
	}
	&__input,
	&__dropdown {
		display: block;
		width: 100%;
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
