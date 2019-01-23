<template lang="pug">
	#app
		.navicon(@click="toggleSideMenu") 🍔
		transition(name="slide-menu")
			SideMenu(
				v-if="isShowingSideMenu" 
				v-on:closeMenu="toggleSideMenu")
		router-view
	</div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import SideMenu from '@/components/SideMenu.vue';

@Component({
	components: {
		SideMenu,
	},
	name: 'App',
})
export default class App extends Vue {
	public static COMPONENTS: string = 'Components';
	public static SINGLE_COMPONENT: string = 'Single Component';
	public isShowingSideMenu: boolean = false;
	public app: HTMLElement | null = null;

	public mounted(): void {
		this.app = document.getElementById('app');
	}

	// public isComponentsPage() {
	// 	console.log(this.$route.name);
	// 	return (
	// 		this.$route.name === App.COMPONENTS ||
	// 		this.$route.name === App.SINGLE_COMPONENT
	// 	);
	// }

	public toggleSideMenu() {
		this.isShowingSideMenu = !this.isShowingSideMenu;

		if (this.isShowingSideMenu === true) {
			this.app!.addEventListener('click', this.closeSideMenu, {
				capture: true,
			});
		}
	}
	public closeSideMenu() {
		this.isShowingSideMenu = false;
		this.app!.removeEventListener('click', this.closeSideMenu);
	}
}
</script>

<style lang="scss">
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	display: flex;
	flex-direction: column;
}
#nav {
	padding: 30px;
	a {
		font-weight: bold;
		color: #2c3e50;
		&.router-link-exact-active {
			color: #42b983;
		}
	}
}
.navicon {
	position: fixed;
	left: 30px;
	top: 30px;
	img {
		width: 30px;
		height: 30px;
	}
}
.slide-menu-enter-active,
.slide-menu-leave-active {
	transition: all 0.3s ease;
}
.slide-menu-enter,
.slide-menu-leave-to {
	transform: translateX(-200px);
}
</style>
