# Redoc Svelte

[![npm](http://img.shields.io/npm/v/redoc-svelte.svg)](https://www.npmjs.com/package/redoc-svelte) [![License](https://img.shields.io/npm/l/redoc-svelte.svg)](https://github.com/matteopolak/redoc-svelte/blob/main/LICENSE)

A drop-in [Svelte](https://svelte.dev) component for [Redoc](https://redocly.com).

> **Note:**
> `redoc-svelte` is not compatible with SvelteKit 1. Please use SvelteKit 2 or later.

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
