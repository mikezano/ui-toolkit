<template lang="pug">
	.home
		img(alt="Vue logo" src="../assets/logo.png")
		HelloWorld(msg="Welcome to Your Vue.js + TypeScript App")
		SideMenu
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import SideMenu from '@/components/SideMenu.vue';

@Component({
	components: {
		HelloWorld,
		SideMenu,
	},
})
export default class Home extends Vue {}
</script>