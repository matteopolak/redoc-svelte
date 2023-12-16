# Redoc Svelte

This is a [Svelte](https://svelte.dev) component for [Redoc](https://redocly.com).

```bash
pnpm add redoc-svelte
yarn add redoc-svelte
npm install redoc-svelte
```

## Usage

For more examples, see the [Redoc documentation](https://redocly.com/docs/redoc/deployment/react/).

```svelte
<script>
  import { RedocStandalone } from 'redoc-svelte';
</script>

<RedocStandalone
  specUrl="https://redocly.github.io/redoc/openapi.yaml"
  options={{
    nativeScrollbars: true,
    theme: { colors: { primary: { main: '#dd5522' } } },
  }}
  on:loaded={e => console.log('loaded', e?.detail)}
/>
```
