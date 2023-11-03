<script lang="ts">
	import '../app.postcss';
	import { initializeStores, Drawer, getDrawerStore } from '@skeletonlabs/skeleton';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
    import Navigation from '$lib/Navigation/Navigation.svelte';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	initializeStores();
	const drawerStore = getDrawerStore();

	function drawerOpen(): void {
		drawerStore.open({});
	}
</script>


<Drawer>
	<Navigation/>
</Drawer>

<!-- App Shell -->
<AppShell slotSidebarLeft="bg-surface-500/5 w-0 lg:w-64">

	<svelte:fragment slot="sidebarLeft">
		<Navigation/>
	</svelte:fragment>

	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<div class="flex items-center">
					<button class="lg:hidden btn btn-sm mr-4" on:click={drawerOpen}>
						<span>
							<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
								<rect width="100" height="20" />
								<rect y="30" width="100" height="20" />
								<rect y="60" width="100" height="20" />
							</svg>
						</span>
					</button>
					<strong class="text-xl uppercase">My UI Portfolio</strong>
				</div>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
