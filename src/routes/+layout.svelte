<script lang="ts">
	// @ts-ignore
	import NProgress from 'nprogress';
	import { beforeNavigate, afterNavigate } from '$app/navigation';
	import '../app.css';

	NProgress.configure({ showSpinner: false });
	beforeNavigate(({}) => {
		NProgress.start();
	});
	afterNavigate(() => {
		NProgress.done();
	});

	let { children } = $props();
</script>

{@render children()}
