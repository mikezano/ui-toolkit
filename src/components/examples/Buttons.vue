<template lang="pug">
	.home
		h1 Buttons
		.message
			| Buttons are used and abused.  I see them misplaced randomly and not
			| consistently.  Explain why the button will do.  It's easy to label
			| something with 'OK' 'Cancel' but writing what it will do gives users
			| more confidence.
		
		ExampleButtonTable
		ExampleButtonForm
		ExampleButtonDialog
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import ExampleButtonDialog from '@/components/examples/buttons/ExampleButtonDialog.vue';
import ExampleButtonForm from '@/components/examples/buttons/ExampleButtonForm.vue';
import ExampleButtonTable from '@/components/examples/buttons/ExampleButtonTable.vue';

@Component({
	components: {
		ExampleButtonDialog,
		ExampleButtonForm,
		ExampleButtonTable,
	},
})
export default class Buttons extends Vue {}
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
