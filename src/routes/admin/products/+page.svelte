<script lang="ts">
	import type { PageData } from './$types';
	import { Input } from '$lib/components/ui/input';
	import { Button } from '$lib/components/ui/button';
	import * as Table from '$lib/components/ui/table';

	let { data }: { data: PageData } = $props();
	let showProducts = $state(true);
</script>

<div class="space-y-4 p-8 pt-6 flex flex-col">
	<div class="flex items-center justify-between space-y-2">
		<h2 class="text-3xl font-bold tracking-tight">产品列表</h2>
		<div class="flex items-center space-x-2">
			<Input class="w-40 lg:w-64" type="text" placeholder="搜索产品" />
			<Button>搜索</Button>
		</div>
	</div>

	{#if !showProducts}
		<Table.Root>
			<Table.Header>
				<Table.Row>
					<Table.Head class="w-[100px]">ID</Table.Head>
					<Table.Head>图像</Table.Head>
					<Table.Head>名称</Table.Head>
					<Table.Head>目录</Table.Head>
					<Table.Head>子目录</Table.Head>
					<Table.Head>价格</Table.Head>
					<Table.Head>库存</Table.Head>
					<Table.Head class="text-right">操作</Table.Head>
				</Table.Row>
			</Table.Header>
			<Table.Body>
				<Table.Row>
					<Table.Cell class="font-medium">1</Table.Cell>
					<Table.Cell
						><img
							src="https://images.stockx.com/360/Air-Jordan-1-Retro-High-OG-Black-Toe-Reimagined-PS/Images/Air-Jordan-1-Retro-High-OG-Black-Toe-Reimagined-PS/Lv2/img21.jpg?w=576&q=57&dpr=2&updated_at=1740500445&h=384"
							alt=""
							class="size-14 rounded border"
						/></Table.Cell
					>
					<Table.Cell>乔丹Air 1</Table.Cell>
					<Table.Cell>鞋类</Table.Cell>
					<Table.Cell>乔丹品牌</Table.Cell>
					<Table.Cell>$0</Table.Cell>
					<Table.Cell>100</Table.Cell>
					<Table.Cell class="text-right">
						<Button variant="destructive">删除</Button>
					</Table.Cell>
				</Table.Row>
			</Table.Body>
		</Table.Root>
		<span class="text-sm mx-auto text-center">共 {data?.products?.length} 条数据</span>
	{:else}
		<p
			class="flex h-[calc(70vh-200px)] w-full flex-col items-center justify-center gap-2 text-center text-sm text-muted-foreground"
		>
			暂无数据
			<Button href="products/add">添加产品</Button>
		</p>
	{/if}
</div>
