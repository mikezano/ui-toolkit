<template lang="pug">
	.example
		.example__title
			slot(name='title')
		.example__bad-reason
			slot(name='bad-reason')
		.example__good-reason
			slot(name='good-reason')
		.example__bad-content
			slot(name='bad-content')
		.example__good-content
			slot(name='good-content')

</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({})
export default class Example extends Vue {}
</script>

<style lang="scss" scoped>
.example {
	width: 52rem;
	padding: 2rem;
	display: grid;
	grid-template-columns: 50% 50%;

	justify-content: space-between;

	&__title {
		grid-row: 1;
		grid-column: 1/3;
		font-weight: bold;
		font-size: 2rem;
		text-align: left;
		margin: 1rem 0;
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
		padding: 1rem;
	}
	&__bad {
	}
}
</style>