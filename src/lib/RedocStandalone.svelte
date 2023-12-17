<script lang="ts">
	import { createRoot, type Root } from 'react-dom/client';
	import { createElement } from 'react';
	import * as redoc from 'redoc';
	import type { RedocRawOptions } from 'redoc';

	import { createEventDispatcher, onMount } from 'svelte';

	export let spec: object | undefined = undefined;
	export let specUrl: string | undefined = undefined;
	export let options: RedocRawOptions | undefined = undefined;

	const dispatch = createEventDispatcher<{ loaded?: Error }>();

	onMount(() => {
		root = createRoot(container);
	});

	$: if (root && container) {
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

	let root: Root | undefined = undefined;
	let container: HTMLDivElement;
</script>

<div bind:this={container} />
