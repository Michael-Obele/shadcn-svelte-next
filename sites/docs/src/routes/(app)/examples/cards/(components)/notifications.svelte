<script lang="ts">
	import Bell from "@lucide/svelte/icons/bell";
	import EyeOff from "@lucide/svelte/icons/eye-off";
	import User from "@lucide/svelte/icons/user";
	import * as Card from "$lib/registry/new-york/ui/card/index.js";
</script>

<Card.Root>
	<Card.Header class="pb-3">
		<Card.Title>Notifications</Card.Title>
		<Card.Description>Choose what you want to be notified about.</Card.Description>
	</Card.Header>
	<Card.Content class="grid gap-1">
		<div
			class="hover:bg-accent hover:text-accent-foreground -mx-2 flex items-start space-x-4 rounded-md p-2 transition-all"
		>
			<Bell class="mt-px size-5" />
			<div class="space-y-1">
				<p class="text-sm font-medium leading-none">Everything</p>
				<p class="text-muted-foreground text-sm">Email digest, mentions & all activity.</p>
			</div>
		</div>
		<div
			class="bg-accent text-accent-foreground -mx-2 flex items-start space-x-4 rounded-md p-2 transition-all"
		>
			<User class="mt-px size-5" />
			<div class="space-y-1">
				<p class="text-sm font-medium leading-none">Available</p>
				<p class="text-muted-foreground text-sm">Only mentions and comments.</p>
			</div>
		</div>
		<div
			class="hover:bg-accent hover:text-accent-foreground -mx-2 flex items-start space-x-4 rounded-md p-2 transition-all"
		>
			<EyeOff class="mt-px size-5" />
			<div class="space-y-1">
				<p class="text-sm font-medium leading-none">Ignoring</p>
				<p class="text-muted-foreground text-sm">Turn off all notifications.</p>
			</div>
		</div>
	</Card.Content>
</Card.Root>
