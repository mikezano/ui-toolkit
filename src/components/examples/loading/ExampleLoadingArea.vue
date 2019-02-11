 <template lang="pug">
div
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
			button#change-table.simple-button(@click='toggleLoader()') Change Table
			#table-area
				table#example-good-table.table(v-if='isShowingPrimaryTable')
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
				table#example-good-table.table(v-else)
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
							td Phoenix
							td AZ
							td U.S.A
						tr.table__row
							td
								.default.btn-circle ✏️
							td Phoenix
							td AZ
							td Pakistan
						tr.table__row
							td
								.default.btn-circle ✏️
							td Phoenix
							td AZ
							td China
						tr.table__row
							td
								.default.btn-circle ✏️
							td Phoenix
							td AZ
							td Japan
		template(slot='bad-content')
	LoaderPane(:focusEl="'table-area'" v-if='isShowingLoaderPane')

</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Example from '@/components/examples/Example.vue';
import LoaderPane from '@/components/LoaderPane.vue';

@Component({
	components: {
		Example,
		LoaderPane,
	},
})
export default class ExampleLoadingArea extends Vue {
	public isShowingLoaderPane: boolean = false;
	public isShowingPrimaryTable: boolean = true;
	public tableName: string = 'table-area';

	public toggleLoader(): void {
		this.isShowingLoaderPane = true;
		setTimeout(() => {
			this.isShowingPrimaryTable = !this.isShowingPrimaryTable;
			this.isShowingLoaderPane = false;
		}, 1000);
	}
}
</script>

<style lang="scss" scoped>
@import 'src/toolkit.scss';
@import 'src/variables.scss';

#example {
	@include simple-form();
}
#change-table {
	@include simpleButton();
}
#loader-div {
	position: fixed;
	background-color: hsla(0, 0, 0, 0.5);
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
