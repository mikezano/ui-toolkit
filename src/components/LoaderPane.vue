<template lang="pug">
#loader-div
	.message {{message}}
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({
	watch: {
		focusEl: 'focusElChanged',
	},
})
export default class LoaderPane extends Vue {
	@Prop() private focusEl!: string;
	@Prop() private message!: string;
	public mounted(): void {
		this.setLoadingRegion(this.focusEl);
	}

	public setLoadingRegion(elementId: string) {
		if (!elementId) return;

		const el: HTMLElement | null = document.getElementById(elementId);

		const rect: ClientRect = el!.getBoundingClientRect();
		const width: number = rect.width;
		const height: number = rect.height;
		const top: number = rect.top;
		const left: number = rect.left;

		const loaderDiv: HTMLElement | null = document.getElementById(
			'loader-div',
		);
		loaderDiv!.style.top = String(top) + 'px';
		loaderDiv!.style.left = String(left) + 'px';
		loaderDiv!.style.width = String(width) + 'px';
		loaderDiv!.style.height = String(height) + 'px';
	}
	public focusElChanged(newEl: string, oldEl: string) {
		debugger;
		if (!newEl) return;

		this.setLoadingRegion(newEl);
	}
}
</script>

<style lang="scss">
#loader-div {
	position: fixed;
	background-color: hsla(0, 0, 0, 0.6);
	display: flex;
	align-items: center;
	justify-content: center;
	.message {
		color: white;
		font-size: 2rem;
		font-weight: bold;
		text-shadow: 0.1rem 0.1rem 0.4rem hsla(0, 0, 0, 0.6);
	}
}
</style>


