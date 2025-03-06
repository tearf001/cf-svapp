<script lang="ts">
    // @ts-ignore    
    import NProgress from 'nprogress';
    import {beforeNavigate, afterNavigate} from '$app/navigation'

    NProgress.configure({ showSpinner: false });
    beforeNavigate(({}) => {
        NProgress.start(); 
    });
    afterNavigate(() => {
        NProgress.done();
    });

</script>
<h1 class="text-3xl">Welcome to SvelteKit</h1>
<p class="text-2xl text-gray-500 container">Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
