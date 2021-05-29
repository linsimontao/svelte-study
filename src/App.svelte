<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';
	import CreatePollsForm from './components/CreatePollsForm.svelte';
	import PollsList from './components/PollsList.svelte';
	
	//tab items
	let items = ['Current Polls', 'Add new Poll'];
	let activeItem = 'Current Polls';

	const tabClick = (item) => activeItem = item.detail;
	
	let polls = [];
	
	const onPollCreate = (poll) => {
		polls = [poll.detail, ...polls];
		activeItem = 'Current Polls';
	}
</script>

<main>
	<Header />
	<Tabs {items} {activeItem} on:tabClick={tabClick} />
	{#if activeItem === 'Add new Poll'}
		<CreatePollsForm on:PollCreate={onPollCreate}/>
	{:else}
		<PollsList {polls}/>
	{/if}
	<Footer />
</main>

<style>
	main {
		max-width: 100%;
		margin: 40px auto;
	}
</style>