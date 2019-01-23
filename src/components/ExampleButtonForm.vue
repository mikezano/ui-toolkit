<template lang="pug">
	Example
		template(slot='title')
			| 2. Usage in Forms
		template(slot='good-reason')
			b Good - 
			span Labels on the left aligned for easy visual scanning
		template(slot='bad-reason')
			b Bad - 
			span Labels next to each other, adds extra width
		template(slot='good-content')
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
		template(slot='bad-content')
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
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/Example.vue';

@Component({
	components: {
		Example,
	},
})
export default class ExampleButtonForm extends Vue {}
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
