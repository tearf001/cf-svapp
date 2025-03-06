<script lang="ts">
    import type { PageData } from './$types';
    import * as Card from "$lib/components/ui/card"
    import * as Table from "$lib/components/ui/table"
    
    
	import { ArrowUpIcon, ShoppingCartIcon } from 'lucide-svelte';
    

    let { data }: { data: PageData } = $props();
</script>

<div class="flex-1 space-y-4 p-8 pt-6">
	<h2 class="text-3xl font-bold tracking-tight">控制台</h2>
	<div class="grid gap-4 md:grid-cols-2 bg-slate-200">
        <Card.Root>
			<Card.Header class="flex flex-row items-center justify-between space-y-0 pb-2">
				<Card.Title class="text-sm font-medium">总计收入</Card.Title>
				<ShoppingCartIcon class="h-4 w-4 text-muted-foreground" />
			</Card.Header>
			<Card.Content>
				<div class="text-2xl font-bold">{(data.totalRevenue|| 5000)}</div>
				<p class="text-xs text-muted-foreground">+{data.revenueGrowth || 25}% 从上个月</p>
			</Card.Content>
		</Card.Root>

		<Card.Root>
			<Card.Header class="flex flex-row items-center justify-between space-y-0 pb-2">
				<Card.Title class="text-sm font-medium">新增用户</Card.Title>
				<ArrowUpIcon class="h-4 w-4 text-muted-foreground" />
			</Card.Header>
			<Card.Content>
				<div class="text-2xl font-bold">+{data.newCustomers||101}</div>
				<p class="text-xs text-muted-foreground">+{data.userGrowth||30}% 从上个月</p>
			</Card.Content>
		</Card.Root>

        <Card.Root class="col-span-5">
            <Card.Header>
                <Card.Title>Recent Orders</Card.Title>
            </Card.Header>
            <Card.Content>
                <Table.Root>
                  <Table.Caption>A list of your recent invoices.</Table.Caption>
                  <Table.Header>
                    <Table.Row>
                      <Table.Head class="w-24">订单</Table.Head>
                      <Table.Head>状态</Table.Head>
                      <Table.Head>客户</Table.Head>
                      <Table.Head class="text-right">金额</Table.Head>
                    </Table.Row>
                  </Table.Header>
                  <Table.Body>
                    <Table.Row>
                      <Table.Cell class="font-medium">INV001</Table.Cell>
                      <Table.Cell>处理中</Table.Cell>
                      <Table.Cell>客户1</Table.Cell>
                      <Table.Cell class="text-right">.00</Table.Cell>
                    </Table.Row>
                  </Table.Body>
                </Table.Root>
            </Card.Content>
        </Card.Root>

    </div>
</div>