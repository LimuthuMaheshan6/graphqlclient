<script lang="ts">
	import './layout.css';
	import Navbar from '$lib/Navbar.svelte';
	 import { QueryClient, QueryClientProvider } from "@sveltestack/svelte-query";
	 const queryClient = new QueryClient()

	const { children } = $props();
</script>

<Navbar></Navbar>
<QueryClientProvider client={queryClient}>
	
	
	{@render children()}
</QueryClientProvider>
