<template lang="pug">
	.home
		h1 Loaders
		.message(style="text-align:left;")
			| Indicating that network calls are being completed tends to be a action we poorly communicate. 
			| Sometimes what starts as a quick call with practically 0 time taken later on blows up 
			| into a long running action. Show a loader!
		
		ExampleLoading
		ExampleLoadingArea
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import ExampleLoading from "@/components/examples/loading/ExampleLoading.vue";
import ExampleLoadingArea from "@/components/examples/loading/ExampleLoadingArea.vue";

@Component({
	components: {
		ExampleLoading,
		ExampleLoadingArea
	}
})
export default class Loaders extends Vue {}
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
