<template lang="pug">
	.home
		h1 Forms
		.message(style="text-align:left;")
			|    Forms easily get out of hand when trying to provide a smorgasbord of options.  Elimainating the cruft
			| will give you back screen space for things that matter.  Form layouts that are
			| not sized equally, when buttons should be disabled, and the interaction after submitting covered here.
		
		ExampleFormUniformity
		ExampleFormExcessFields
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import ExampleFormUniformity from '@/components/examples/forms/ExampleFormUniformity.vue';
import ExampleFormExcessFields from '@/components/examples/forms/ExampleFormExcessFields.vue';

@Component({
	components: {
		ExampleFormUniformity,
		ExampleFormExcessFields,
	},
})
export default class Forms extends Vue {}
</script>

<style lang="scss" scoped>
.home {
	display: flex;
	flex-direction: column;
	align-items: center;
}
.message {
	width: 50rem;
}
</style>
