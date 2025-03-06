<script lang="ts">
	import type { PageData } from './$types';
	import * as Form from '$lib/components/ui/form';
	import * as Card from '$lib/components/ui/card';
	import { Button } from '$lib/components/ui/button';
	import { Input } from '$lib/components/ui/input';

	let { data }: { data: PageData } = $props();
</script>

<div class="space-y-4 p-8">
	<div class="flex flex-col items-center justify-between space-y-2">
		<h2 class="text-3xl font-bold tracking-tight">创建产品</h2>
		<div class="flex items-center space-x-2">
			<a href="/products/add" class="btn">创建</a>
		</div>
		<form action="" enctype="multipart/form-data" method="POST">
			<Card.Root class="container">
				<Card.Header>
					<Card.Title>产品信息</Card.Title>
					<Card.Description>请填写产品信息</Card.Description>
				</Card.Header>
				<Card.Content>
					<Form.Field {form} name="email">
						<Form.Control>
							{#snippet children({ props })}
								<Form.Label>Email</Form.Label>
								<Input {...props} bind:value={formData.email} />
							{/snippet}
						</Form.Control>
						<Form.Description />
						<Form.FieldErrors />
					</Form.Field>
				</Card.Content>
				<Card.Footer>
					<Button>提交</Button>
				</Card.Footer>
			</Card.Root>
		</form>
	</div>
</div>
