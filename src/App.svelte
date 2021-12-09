<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import Tabs from "./shared/Tabs.svelte";

	//tabs
	let tabs = ['Current Polls', 'Add New Poll'];
	let activeTab = 'Current Polls';

	const tabChange = (e) => {
		activeTab = e.detail;
	}
</script>

<Header />
<main>
	<Tabs {activeTab} {tabs} on:tabChange={tabChange} />
	{#if activeTab === 'Current Polls'}
		<p>Poll list component</p>
	{:else if activeTab === 'Add New Poll'}
		<p>New poll</p>
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
