<script lang="ts">
	import * as Sidebar from '$lib/components/ui/sidebar/index.js';
	import { Blocks, Box, Home, Truck, User, LayoutDashboard } from 'lucide-svelte';

	// Menu items.
	const items = [
		{
			title: '概览',
			url: 'overview',
			icon: LayoutDashboard
		},
		{
			title: '产品',
			url: 'products',
			icon: Box
		},
		{
			title: '用户',
			url: 'users',
			icon: User
		},
		{
			title: '订单',
			url: 'order',
			icon: Truck
		},
		{
			title: '分类',
			url: 'categories',
			icon: Blocks
		},
		{
			title: '工作台',
			url: '../',
			icon: Home
		}
	];

	let { children } = $props();
</script>

<Sidebar.Provider>
	<Sidebar.Root>
		<Sidebar.Content>
			<Sidebar.Group>
				<Sidebar.GroupLabel>应用程序</Sidebar.GroupLabel>
				<Sidebar.GroupContent>
					<Sidebar.Menu>
						{#each items as item (item.title)}
							<Sidebar.MenuItem>
								<Sidebar.MenuButton>
									{#snippet child({ props })}
										<a href={'/admin/' + item.url} {...props}>
											<item.icon />
											<span>{item.title}</span>
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
	<main class="flex-1">
		<Sidebar.Trigger />
		{@render children?.()}
	</main>
</Sidebar.Provider>
