 <template lang="pug">
div
	#loader-div
	Example
		template(slot='title')
			| 2. Indicate what's going to change
		template(slot='good-reason')
			b Good - 
			span Changing a value in one area affects the other.  This needs to be 
			| clearly indicated
		template(slot='bad-reason')
			b Not as good - 
			span A change in one area causes
		template(slot='good-content')
			select
				option A
				option B
				option C
			table#example-good-table.table
				thead
					tr
						th Action
						th City
						th State
						th Country
				tbody
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td U.S.A
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td Pakistan
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td China
					tr.table__row
						td
							.default.btn-circle ✏️
						td Scottsdale
						td AZ
						td Japan
		template(slot='bad-content')

</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/examples/Example.vue';

@Component({
	components: {
		Example,
	},
})
export default class ExampleLoadingArea extends Vue {
	public mounted(): void {
		var el: HTMLElement | null = document.getElementById(
			'#example-good-table',
		);
		var rect: ClientRect = el!.getBoundingClientRect();
		var width: number = rect.width;
		var height: number = rect.height;
		var top: number = rect.top;
		var left: number = rect.left;

		var loaderDiv: HTMLElement | null = document.getElementById(
			'#loader-div',
		);

		loaderDiv!.style.top = String(top);
		loaderDiv!.style.left = String(left);
		loaderDiv!.style.width = String(width) + 'px';
		loaderDiv!.style.height = String(height) + 'px';
	}
}
</script>

<style lang="scss" scoped>
@import 'src/toolkit.scss';
@import 'src/variables.scss';

#example {
	@include simple-form();
}
#loader-div {
	position: absolute;
}

.table {
	border-collapse: collapse;
	&__row:hover {
		background-color: whitesmoke;
	}
	th {
		background-image: linear-gradient($main, $mainL1);
	}
	td,
	th {
		border-bottom: 0.1rem solid lightgray;
		padding: 0.2rem 1rem;
	}
}
</style>
