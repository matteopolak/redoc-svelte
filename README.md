# Redoc Svelte

[![npm](http://img.shields.io/npm/v/redoc-svelte.svg)](https://www.npmjs.com/package/redoc-svelte) [![License](https://img.shields.io/npm/l/redoc-svelte.svg)](https://github.com/matteopolak/redoc-svelte/blob/main/LICENSE)

A drop-in [Svelte](https://svelte.dev) component for [Redoc](https://redocly.com).

```bash
pnpm add redoc-svelte
yarn add redoc-svelte
npm install redoc-svelte
```

> [!IMPORTANT]
> `redoc-svelte` is not compatible with SvelteKit v1, please use v2 instead.

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

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
