<script lang="ts">
	import type { SidebarNavItem } from "$lib/types/nav.js";
	import { page } from "$app/state";
	import { cn } from "$lib/utils.js";

	let { items }: { items: SidebarNavItem[] } = $props();
</script>

{#if items.length}
	<div class="grid grid-flow-row auto-rows-max text-sm">
		{#each items as item, index (index)}
			{#if item.href}
				<a
					href={item.href}
					class={cn(
						"group flex w-full items-center rounded-md border border-transparent px-2 py-1 hover:underline",
						item.disabled && "cursor-not-allowed opacity-60",
						page.url.pathname === item.href
							? "text-foreground font-medium"
							: "text-muted-foreground"
					)}
					target={item.external ? "_blank" : ""}
					rel={item.external ? "noreferrer" : ""}
				>
					{item.title}
					{#if item.label}
						<span
							class="ml-2 rounded-md bg-[#adfa1d] px-1.5 py-0.5 text-xs leading-none text-[#000000] no-underline group-hover:no-underline"
						>
							{item.label}
						</span>
					{/if}
				</a>
			{:else}
				<span
					class="text-muted-foreground flex w-full cursor-not-allowed items-center rounded-md p-2 hover:underline"
				>
					{item.title}
				</span>
			{/if}
		{/each}
	</div>
{/if}
