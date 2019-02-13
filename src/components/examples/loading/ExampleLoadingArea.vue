 <template lang="pug">
div
	Example
		template(slot='title')
			| 2. Clearly indicate what will change
		template(slot='good-reason')
			b Good - 
			span Clicking the 'Change Table' button here creates an action 
			| to bring to the users attention that new content is coming into the table.
		template(slot='bad-reason')
			b Not so good - 
			span A click of the 'Change Table' button switches out the table 
			| with new content, but if you blink, you may miss the fact that 
			| it changed!
		template(slot='good-content')
			button#change-table.simple-button(@click='toggleLoader()') Change Table
			#table-area
				div(style="margin-top:1rem;") Largest World Populations
				table#example-good-table.table(v-if='isShowingPrimaryTable')
					thead
						tr
							th Population
							th City
							th Country
							th 
					tbody
						tr.table__row
							td 37.5
							td Tokyo
							td Japan
							td 🇯🇵
						tr.table__row
							td 28.5
							td Delhi
							td India
							td 🇮🇳
						tr.table__row
							td 25.6
							td Shanghai
							td China
							td 🇨🇳
						tr.table__row
							td 21.7
							td Sao Paulo
							td Brazil
							td 🇧🇷
						tr.table__row
							td 21.6
							td Mexico City
							td Mexico
							td 🇲🇽
				table#example-good-table.table(v-else)
					thead
						tr
							th Population
							th Country
							th 
					tbody
						tr.table__row
							td 1.4 B
							td China
							td 🇨🇳
						tr.table__row
							td 1.3 B
							td India
							td 🇮🇳
						tr.table__row
							td 329 M
							td United States
							td 🇨🇳
						tr.table__row
							td 269 M
							td Indonesia
							td 🇧🇷
						tr.table__row
							td 212 M
							td Brazil
							td 🇧🇷
		template(slot='bad-content')
			button#change-table.simple-button(@click='toggleUsTables()') Change Table
			div(style="margin-top:1rem;") Largest U.S. Populations
			table#example-good-table.table(v-if='isShowingByUsCity')
				thead
					tr
						th Population
						th City
						th State
				tbody
					tr.table__row
						td 8.6
						td New York
						td New York
					tr.table__row
						td 3.9
						td Los Angeles
						td California
					tr.table__row
						td 2.7
						td Chicago
						td Illinois
					tr.table__row
						td 2.3
						td Houston
						td Texas
					tr.table__row
						td 1.6
						td Phoenix
						td Arizona
			table#example-good-table.table(v-else)
				thead
					tr
						th Population
						th State
				tbody
					tr.table__row
						td 39.7
						td California
					tr.table__row
						td 28.7
						td Texas
					tr.table__row
						td 21.1
						td Florida
					tr.table__row
						td 19.8
						td New York
					tr.table__row
						td 12.8
						td Pennsylvania
	transition(name="fade")
		LoaderPane(:focusEl="'table-area'"  :message="'Loading'" v-if='isShowingLoaderPane')

</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Example from "@/components/examples/Example.vue";
import LoaderPane from "@/components/LoaderPane.vue";

@Component({
	components: {
		Example,
		LoaderPane
	}
})
export default class ExampleLoadingArea extends Vue {
	public isShowingLoaderPane: boolean = false;
	public isShowingPrimaryTable: boolean = true;
	public isShowingByUsCity: boolean = true;
	public tableName: string = "table-area";

	public toggleUsTables(): void {
		setTimeout(() => {
			this.isShowingByUsCity = !this.isShowingByUsCity;
		}, 3000);
	}
	public toggleLoader(): void {
		this.isShowingLoaderPane = true;
		setTimeout(() => {
			this.isShowingPrimaryTable = !this.isShowingPrimaryTable;
			this.isShowingLoaderPane = false;
		}, 3000);
	}
}
</script>

<style lang="scss" scoped>
@import "src/toolkit.scss";
@import "src/variables.scss";

.fade-enter-active,
.fade-leave-active {
	transition: opacity 0.1s ease-in;
}
.fade-enter,
.fade-leave-to {
	opacity: 0;
}
.fade-enter-to,
.fade-leave {
	opacity: 1;
}

#example {
	@include simple-form();
}
#change-table {
	@include simpleButton();
}

#example-good-table {
	width: 100%;
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
