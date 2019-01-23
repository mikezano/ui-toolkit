<template lang="pug">
	Example
		template(slot='title')
			| 1. Usage in Tables
		template(slot='good-reason')
			b Good - 
			span Show your action items on the left side of the table so that they are immediately available to user
		template(slot='bad-reason')
			b Bad - 
			| Action items are located in the middle of the table, breaking up data
		template(slot='good-content')
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
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td U.S.A
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td Pakistan
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td China
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td Japan
		template(slot='bad-content')
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
							.default.btn-circle ✏️
							.default.btn-circle 🗑️
						td U.S.A
					tr.table__row
						td Scottsdale
						td AZ
						td
							.default.btn-circle ✏️
							.default.btn-circle 🗑️
						td Pakistan
					tr.table__row
						td Scottsdale
						td AZ
						td
							.default.btn-circle ✏️
							.default.btn-circle 🗑️
						td China
					tr.table__row
						td Scottsdale
						td AZ
						td
							.default.btn-circle ✏️
							.default.btn-circle 🗑️
						td Japan
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Example from "@/components/examples/Example.vue";

@Component({
	components: {
		Example
	}
})
export default class ExampleButtonTable extends Vue {}
</script>

<style lang="scss" scoped>
@import "src/toolkit.scss";
@import "src/variables.scss";

.default {
	@include btn-circle(white, 14px);
	float: left;
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
</style>
