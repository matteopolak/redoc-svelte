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
		redoc = await import('redoc');
		root = createRoot(container);
	});

	$: if (root && container && redoc) {
		root.render(
			createElement(redoc.RedocStandalone, {
				spec,
				specUrl,
				options,
				onLoaded: (e?: Error) => {
					dispatch('loaded', e);
				},
			}),
		);
	}

	let redoc: typeof import('redoc') | undefined = undefined;
	let root: Root | undefined = undefined;
	let container: HTMLDivElement;
</script>

<div bind:this={container} />
