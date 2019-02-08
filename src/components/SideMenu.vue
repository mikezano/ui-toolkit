<template lang="pug">
	.side-menu
		.side-menu__close(@click="close")
			icon(name="close" class="close-icon")
		.side-menu__header
			img(src="./../assets/logo.png")
			router-link(to="/style_guide" tag="p") gUIde
		
		.side-menu__sections

			.side-menu__section-header When you use...
			ul.side-menu__section-list
				router-link(to="/buttons" tag="li") Buttons
				router-link(to="/forms" tag="li") Forms
				router-link(to="/loaders" tag="li") Loaders


			.side-menu__section-header Sample Site
			ul.side-menu__section-list
				router-link(to="/style_guide/grid_layouts" tag="li") Countries of the world

			.side-menu__section-header More Resources
			ul.side-menu__section-list
				router-link(to="/bem", tag="li") UI Toolkit
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({})
export default class SideMenu extends Vue {
	public close() {
		this.$emit('closeMenu');
	}
}
</script>

<style lang="scss">
@import 'src/variables.scss';
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
	top: 0;
	bottom: 0;

	//background-image: linear-gradient($mainD1, $mainD2);
	background-color: $mainL1;

	//color: white;
	//padding-left: 1rem;

	box-shadow: 1rem 1rem 2rem hsla(0, 0, 0, 0.2);
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
		padding: 0.4rem 0;
		margin: 0 1rem;
		border-top: 0.1rem solid $mainD2;
		font-size: 1rem;
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
		font-size: 1rem;
		&:hover {
			cursor: pointer;
		}
	}
}
</style>


