<script lang="ts">
	import type { RedocRawOptions } from 'redoc';
	import { createEventDispatcher, onMount } from 'svelte';
	import { createRoot } from 'react-dom/client';
	import { createElement } from 'react';

	export let spec: object | undefined = undefined;
	export let specUrl: string | undefined = undefined;
	export let options: RedocRawOptions | undefined = undefined;

	const dispatch = createEventDispatcher<{ loaded?: Error }>();

	onMount(async () => {
		const { RedocStandalone } = await import('redoc');

		const root = createRoot(container);

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
	});

	let container: HTMLDivElement;
</script>

<div bind:this={container} />
