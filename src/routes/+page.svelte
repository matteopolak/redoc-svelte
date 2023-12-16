<script lang="ts">
	import RedocStandalone from '$lib/RedocStandalone.svelte';
</script>

<RedocStandalone
	specUrl="https://redocly.github.io/redoc/openapi.yaml"
	options={{
		nativeScrollbars: true,
		theme: { colors: { primary: { main: '#dd5522' } } },
	}}
	on:loaded={e => console.log('loaded', e?.detail)}
/>
