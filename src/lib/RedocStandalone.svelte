<script lang="ts">
	import { createRoot, type Root } from 'react-dom/client';
	import { createElement } from 'react';
	import type { RedocRawOptions } from 'redoc';

	import { createEventDispatcher, onMount } from 'svelte';

	export let spec: object | undefined = undefined;
	export let specUrl: string | undefined = undefined;
	export let options: RedocRawOptions | undefined = undefined;

	const dispatch = createEventDispatcher<{ loaded?: Error }>();

	onMount(async () => {
		root = createRoot(container);
		RedocStandalone = await import('redoc').then(m => m.RedocStandalone);
	});

	$: if (root && container && RedocStandalone) {
		root.render(
			createElement(RedocStandalone, {
				spec,
				specUrl,
				options,
				onLoaded: (e?: Error) => {
					dispatch('loaded', e);
				},
			}),
		);
	}

	let RedocStandalone: typeof import('redoc').RedocStandalone | undefined =
		undefined;
	let root: Root | undefined = undefined;
	let container: HTMLDivElement;
</script>

<div bind:this={container} />
