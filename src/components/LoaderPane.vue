<template lang="pug">
#loader-div
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

	public mounted(): void {
		debugger;
	}

	public focusElChanged(newEl: string, oldEl: string) {
		debugger;
		if (!newEl) return;

		const el: HTMLElement | null = document.getElementById(newEl);

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
}
</script>

<style lang="scss">
</style>


