<template lang="pug">
	.side-menu
		.side-menu__close(@click="close")
			icon(name="close" class="close-icon")
		.side-menu__header
			img(src="./../assets/logo.png")
			router-link(to="/style_guide" tag="p") Style Guide
		
		.side-menu__sections
			.side-menu__section-header Usage
			ul.side-menu__section-list
				router-link(to="/how_to_use" tag="li") How to use
				router-link(to="/test" tag="li") Test

			.side-menu__section-header How to use...
			ul.side-menu__section-list
				router-link(to="/buttons" tag="li") Buttons
				router-link(to="/forms" tag="li") Forms


			.side-menu__section-header Sample Site
			ul.side-menu__section-list
				router-link(to="/style_guide/grid_layouts" tag="li") CSS Grid

			.side-menu__section-header More Resources
			ul.side-menu__section-list
				router-link(to="/bem", tag="li") UI Toolkit
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({})
export default class SideMenu extends Vue {
	public close() {
		this.$emit("closeMenu");
	}
}
</script>

<style lang="scss">
@import "src/variables.scss";
$base1: hsla(153, 50%, 48%, 1);
$base2: hsla(211, 28%, 29%, 1);

.close-icon {
	position: absolute;
	right: 0;
	margin: 10px 10px 0 0;
}

.side-menu {
	width: 14rem;
	position: fixed;
	z-index: 100;
	left: 0;
	top: 3rem;

	background-image: linear-gradient($mainD1, $mainD2);
	//background-color: $main;

	//color: white;
	//padding-left: 1rem;

	box-shadow: 2px 2px 4px gray;
	&__header {
		padding: 1rem 0;
		//margin-left: 0rem;
		display: flex;
		justify-content: center;
		align-items: center;

		img {
			width: 30px;
			height: 30px;
			transition: transform 0.3s ease-out;
		}
		&:hover {
			cursor: pointer;
			text-decoration: underline;
			img {
				transform: rotateY(180deg);
			}
		}
	}

	&__section-header {
		font-weight: bold;
		text-align: left;
		padding: 1rem 0 1rem 1rem;
		//border-top: 0.1rem solid $mainD2;
	}

	&__section-list {
		list-style-type: none;
		margin: 0;
		padding: 0;
		padding-left: 1rem;
		margin-bottom: 1rem;
		text-align: left;
	}
	li {
		padding: 5px 0;
		font-size: 0.8rem;
		&:hover {
			cursor: pointer;
		}
	}
}
</style>


