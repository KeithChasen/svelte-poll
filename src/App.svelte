<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import Tabs from "./shared/Tabs.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import PollList from "./components/PollList.svelte";

	//tabs
	let tabs = ['Current Polls', 'Add New Poll'];
	let activeTab = 'Current Polls';

	const tabChange = (e) => {
		activeTab = e.detail;
	}

	const handleAddPoll = (e) => {
		activeTab = 'Current Polls';
	}

	const handleVote = (e) => {
		const { id, option } = e.detail;
		const copiedPolls = [...polls];
		const upvotedPoll = copiedPolls.find(poll => poll.id === id);
		if (option === 'a') {
			upvotedPoll.votesA++
		}
		if (option === 'b') {
			upvotedPoll.votesB++
		}
		polls = copiedPolls;
	}
</script>

<Header />
<main>
	<Tabs {activeTab} {tabs} on:tabChange={tabChange} />
	{#if activeTab === 'Current Polls'}
		<PollList on:vote={handleVote}/>
	{:else if activeTab === 'Add New Poll'}
		<CreatePollForm on:addPoll={handleAddPoll} />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
