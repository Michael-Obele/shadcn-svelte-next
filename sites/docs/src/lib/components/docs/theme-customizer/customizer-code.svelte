<script lang="ts">
	import { config } from "$lib/stores/index.js";
	import { themes } from "$lib/registry/index.js";
	import ThemeWrapper from "$lib/components/docs/theme-wrapper.svelte";

	const activeTheme = $derived(themes.find((theme) => theme.name === $config.theme));

	let { setCodeString }: { setCodeString: (node: HTMLElement) => void } = $props();

	const prefixes = [
		"card",
		"popover",
		"primary",
		"secondary",
		"muted",
		"accent",
		"destructive",
	] as const;
</script>

<ThemeWrapper defaultTheme="zinc" class="relative space-y-4">
	<div data-rehype-pretty-code-fragment="">
		<pre
			class="max-h-[450px] overflow-x-auto rounded-lg border bg-zinc-950 dark:bg-zinc-900"
			use:setCodeString>
            <code class="bg-muted relative rounded px-[0.3rem] py-[0.2rem] font-mono text-sm">
                <span class="line text-white">@layer base &#123;</span>
                <span class="line text-white">  :root &#123;</span>
                <span class="line text-white">    --background: {activeTheme?.cssVars.light
						.background};</span
				>
            <span class="line text-white">    --foreground: {activeTheme?.cssVars.light
						.foreground};</span
				>
            {#each prefixes as prefix (prefix)}
					<span class="line text-white">    --{prefix}: {activeTheme?.cssVars.light[
							prefix
						]};</span
					>
              <span
						class="line text-white">    --{prefix}-foreground: {activeTheme?.cssVars
							.light[`${prefix}-foreground`]};</span
					>
				{/each}
                <span class="line text-white">    --border: {activeTheme?.cssVars.light
						.border};</span
				>
                  <span class="line text-white">    --input: {activeTheme?.cssVars.light
						.input};</span
				>
                  <span class="line text-white">    --ring: {activeTheme?.cssVars.light.ring};</span
				>
                  <span class="line text-white">    --radius: {$config.radius}rem;</span>
                  <span class="line text-white">  &#125;</span>
                  <span class="line text-white"></span>
                  <span class="line text-white">  .dark &#123;</span>
                  <span class="line text-white">    --background: {activeTheme?.cssVars.dark
						.background};</span
				>
                  <span class="line text-white">    --foreground: {activeTheme?.cssVars.dark
						.foreground};</span
				>
                  {#each prefixes as prefix (prefix)}
					<span class="line text-white">    --{prefix}: {activeTheme?.cssVars.dark[
							prefix
						]};</span
					>
            <span
						class="line text-white">    --{prefix}-foreground: {activeTheme?.cssVars
							.dark[`${prefix}-foreground`]};</span
					>
				{/each}
                <span class="line text-white">    --border: {activeTheme?.cssVars.dark
						.border};</span
				>
                  <span class="line text-white">    --input: {activeTheme?.cssVars.dark
						.input};</span
				>
                  <span class="line text-white">    --ring: {activeTheme?.cssVars.dark.ring};</span>
                  <span class="line text-white">  &#125;</span>
                  <span class="line text-white">&#125;</span>
            </code>
        </pre>
	</div>
</ThemeWrapper>
