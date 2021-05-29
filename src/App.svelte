<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';
	import CreatePollsForm from './components/CreatePollsForm.svelte';
	
	//tab items
	let items = ['Current Polls', 'Add new Poll'];
	let activeItem = 'Current Polls';

	const tabClick = (item) => activeItem = item.detail;
</script>

<main>
	<Header />
	<Tabs {items} {activeItem} on:tabClick={tabClick} />
	<CreatePollsForm />
	<Footer />
</main>

<style>
	main {
		max-width: 100%;
		margin: 40px auto;
	}
</style>