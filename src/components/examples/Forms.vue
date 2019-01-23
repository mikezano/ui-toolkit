<template lang="pug">
	.home
		h1 Forms
		.message
			| Forms come with a variety of problem themselves.  Inputs are
			| not sized equally, buttons get disabled, layouts are not uniform.
		
		ExampleFormUniformity
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import ExampleFormUniformity from "@/components/examples/forms/ExampleFormUniformity.vue";

@Component({
	components: {
		ExampleFormUniformity
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
