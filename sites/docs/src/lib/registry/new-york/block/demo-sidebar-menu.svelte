<script lang="ts">
	import * as Sidebar from "$lib/registry/new-york/ui/sidebar/index.js";
	import LifeBuoy from "@lucide/svelte/icons/life-buoy";
	import Send from "@lucide/svelte/icons/send";
	import Frame from "@lucide/svelte/icons/frame";
	import ChartPie from "@lucide/svelte/icons/chart-pie";
	import Map from "@lucide/svelte/icons/map";
	const projects = [
		{
			name: "Design Engineering",
			url: "#",
			icon: Frame,
		},
		{
			name: "Sales & Marketing",
			url: "#",
			icon: ChartPie,
		},
		{
			name: "Travel",
			url: "#",
			icon: Map,
		},
		{
			name: "Support",
			url: "#",
			icon: LifeBuoy,
		},
		{
			name: "Feedback",
			url: "#",
			icon: Send,
		},
	];
</script>

<Sidebar.Provider>
	<Sidebar.Root>
		<Sidebar.Content>
			<Sidebar.Group>
				<Sidebar.GroupLabel>Projects</Sidebar.GroupLabel>
				<Sidebar.GroupContent>
					<Sidebar.Menu>
						{#each projects as project (project.name)}
							<Sidebar.MenuItem>
								<Sidebar.MenuButton>
									{#snippet child({ props })}
										<a href={project.url} {...props}>
											<project.icon />
											<span>{project.name}</span>
										</a>
									{/snippet}
								</Sidebar.MenuButton>
							</Sidebar.MenuItem>
						{/each}
					</Sidebar.Menu>
				</Sidebar.GroupContent>
			</Sidebar.Group>
		</Sidebar.Content>
	</Sidebar.Root>
</Sidebar.Provider>
