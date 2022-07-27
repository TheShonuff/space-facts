<script lang="ts">
	import DesktopNav from './DesktopNav.svelte';
	import MobileNav from './MobileNav.svelte';
	import { menu } from './Stores';

	let menuValue;

	menu.subscribe((value) => {
		menuValue = value;
	});
</script>

<DesktopNav {menuValue} />

<slot />
