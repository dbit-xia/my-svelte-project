<script>
	import SvelteTable from "./SvelteTable.svelte";
	const rows = [
		{ id: 1, first_name: "Marilyn", last_name: "Monroe", gender: "female" },
		{ id: 2, first_name: "Abraham", last_name: "Lincoln", gender: "male" },
		{ id: 3, first_name: "Mother", last_name: "Teresa", gender: "female" },
		{ id: 4, first_name: "John F.", last_name: "Kennedy", gender: "male" },
		{ id: 5, first_name: "Martin Luther", last_name: "King", gender: "male" },
		{ id: 6, first_name: "Nelson", last_name: "Mandela", gender: "male" },
		{ id: 7, first_name: "Winston", last_name: "Churchill", gender: "male" },
		{ id: 8, first_name: "George", last_name: "Soros", gender: "male" },
		{ id: 9, first_name: "Bill", last_name: "Gates", gender: "male" },
		{ id: 10, first_name: "Muhammad", last_name: "Ali", gender: "male" },
		{ id: 11, first_name: "Mahatma", last_name: "Gandhi", gender: "male" },
		{ id: 12, first_name: "Margaret", last_name: "Thatcher", gender: "female" },
		{ id: 13, first_name: "Christopher", last_name: "Columbus", gender: "male" },
		{ id: 14, first_name: "Charles", last_name: "Darwin", gender: "male" },
		{ id: 15, first_name: "Elvis", last_name: "Presley", gender: "male" },
		{ id: 16, first_name: "Albert", last_name: "Einstein", gender: "male" },
		{ id: 17, first_name: "Paul", last_name: "McCartney", gender: "male" },
		{ id: 18, first_name: "Queen", last_name: "Victoria", gender: "female" },
		{ id: 19, first_name: "Pope", last_name: "Francis", gender: "male" }
		// etc...
	];

	// define column configs
	const columns = [
		{
			key: "id",
			title: "ID",
			value: v => v.id,
			sortable: true,
			// filterOptions: rows => {
			// 	// generate groupings of 0-10, 10-20 etc...
			// 	let nums = {};
			// 	rows.forEach(row => {
			// 		let num = Math.floor(row.id / 10);
			// 		if (nums[num] === undefined)
			// 			nums[num] = { name: `${num * 10} to ${(num + 1) * 10}`, value: num };
			// 	});
			// 	// fix order
			// 	nums = Object.entries(nums)
			// 			.sort()
			// 			.reduce((o, [k, v]) => ((o[k] = v), o), {});
			// 	return Object.values(nums);
			// },
			filterValue: v => Math.floor(v.id / 10),
			headerClass: "bordClass"
		},
		{
			key: "first_name",
			title: "FIRST_NAME",
			value: v => v.first_name,
			sortable: true,
			// filterOptions: rows => {
			// 	// use first letter of first_name to generate filter
			// 	let letrs = {};
			// 	rows.forEach(row => {
			// 		let letr = row.first_name.charAt(0);
			// 		if (letrs[letr] === undefined)
			// 			letrs[letr] = {
			// 				name: `${letr.toUpperCase()}`,
			// 				value: letr.toLowerCase()
			// 			};
			// 	});
			// 	// fix order
			// 	letrs = Object.entries(letrs)
			// 			.sort()
			// 			.reduce((o, [k, v]) => ((o[k] = v), o), {});
			// 	return Object.values(letrs);
			// },
			filterValue: v => v.first_name.charAt(0).toLowerCase(),
			headerClass: "bordClass"
		},
		{
			key: "last_name",
			title: "LAST_NAME",
			value: v => v.last_name,
			sortable: true,
			// filterOptions: rows => {
			// 	// use first letter of last_name to generate filter
			// 	let letrs = {};
			// 	rows.forEach(row => {
			// 		let letr = row.last_name.charAt(0);
			// 		if (letrs[letr] === undefined)
			// 			letrs[letr] = {
			// 				name: `${letr.toUpperCase()}`,
			// 				value: letr.toLowerCase()
			// 			};
			// 	});
			// 	// fix order
			// 	letrs = Object.entries(letrs)
			// 			.sort()
			// 			.reduce((o, [k, v]) => ((o[k] = v), o), {});
			// 	return Object.values(letrs);
			// },
			filterValue: v => v.last_name.charAt(0).toLowerCase(),
			headerClass: "bordClass"
		},
		{
			key: "gender",
			title: "GENDER",
			value: v => v.gender,
			renderValue: v => v.gender.charAt(0).toUpperCase() + v.gender.substring(1), // capitalize
			sortable: true,
			// filterOptions: ["male", "female"] // provide array
			headerClass: "bordClass"
		}
	];
	
    import Test02 from './Test02.svelte';
	export let name;
	export let visible=false;
	const handleClick=()=>{
		name=123;
		visible=true;
	}

	
</script>

<SvelteTable columns="{columns}" rows="{rows}" classNameRow="bordClass" ></SvelteTable>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button on:click={handleClick}>OK</button>
</main>

<style>
	
	:global(.bordClass) {
		border-collapse: collapse;
		border: #999999 1px solid;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
{#if visible}
	<Test02 name={name}/>
{/if}
