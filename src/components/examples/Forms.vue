<template lang="pug">
	.home
		h1 Forms
		.message
			| Forms come with a variety of problem themselves.  Inputs are
			| not sized equally, buttons get disabled, layouts are not uniform.
		
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
