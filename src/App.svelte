<script>
	import Header from "./Header.svelte";
	import Input from "./Input.svelte";
	import IncomeEntry from "./UI/IncomeEntry.svelte";
	import ExpenseEntry from "./UI/ExpenseEntry.svelte";

	let entries = [];

	let totalEarnedArray = [];
	let totalEarnedSum = 0;

	let totalSavedArray = [];
	let totalSavedSum = 0;

	let totalAvailableArray = [];
	let totalAvailableSum = 0;

	function totalEntry(event) {
		const newAmountEntry = parseFloat(event.detail.amount);
		totalEarnedArray = [newAmountEntry, ...totalEarnedArray];
		totalEarnedSum += totalEarnedArray[0];
		totalEarnedSum = parseFloat(totalEarnedSum.toFixed(2));

		const savingsPerc = parseFloat(event.detail.savingsPerc);
		const newSavingsEntry = newAmountEntry * savingsPerc;
		totalSavedArray = [newSavingsEntry, ...totalSavedArray];
		totalSavedSum += totalSavedArray[0];
		totalSavedSum = parseFloat(totalSavedSum.toFixed(2));

		const newAvailableEntry = newAmountEntry * (1 - savingsPerc);
		totalAvailableArray = [newAvailableEntry, ...totalAvailableArray];
		totalAvailableSum += totalAvailableArray[0];
		totalAvailableSum = parseFloat(totalAvailableSum.toFixed(2));
	}

	function addEntry(event) {
		const newEntry = {
			date: event.detail.date,
			amount: event.detail.amount,
			savingsPerc: event.detail.savingsPerc,
			title: event.detail.title,
		};

		entries = [newEntry, ...entries];
	}
</script>

<main class="w-full h-full bg-gray-800 p-12">
	<Header
		name="Nico"
		totalEarned={totalEarnedSum}
		totalSavings={totalSavedSum}
		totalAvailable={totalAvailableSum} />
	<Input on:save={addEntry} on:total={totalEntry} />

	<div class="flex items-center flex-col h-full">
		{#each entries as entry}
			{#if entry.amount < 0}
				<ExpenseEntry
					date={entry.date}
					amount={entry.amount}
					title={entry.title} />
			{:else}
				<IncomeEntry
					date={entry.date}
					amount={entry.amount}
					savingsPerc={entry.savingsPerc}
					title={entry.title} />
			{/if}
		{/each}
	</div>
</main>
