<template lang="pug">
	.home
		h1 Forms
		.message
			| Forms asily get out of hand when trying to provide a buffet.  Elimainating the cruft
			| will make it asier to us and giv you back screen space for things that matter.  Form layouts that are
			| not sized equally, when buttons get disabled, and the interaction after proceding are covered here.
		
		ExampleFormUniformity
		ExampleFormExcessFields
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import ExampleFormUniformity from "@/components/examples/forms/ExampleFormUniformity.vue";
import ExampleFormExcessFields from "@/components/examples/forms/ExampleFormExcessFields.vue";

@Component({
	components: {
		ExampleFormUniformity,
		ExampleFormExcessFields
	}
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
