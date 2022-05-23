<script>
	import BaseLayout from './Layouts/BaseLayout.svelte';
	import Header from './Partials/Header.svelte';
	import Footer from './Partials/Footer.svelte';
</script>


<BaseLayout>
	<div slot="header">
		<Header/>
	</div>
	<main>
		
	</main>
	<div slot="footer">
		<Footer/>
	</div>
</BaseLayout>

<style lang="postcss" global>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
