<script>
	import ContactCard from "./ContactCard.svelte";

	let name = "";
	let age = 30;
	let jobtitle = "";
	let shortDescription = "";
	let userImage = "https://nyrami.com/assets/team/alpy.jpg";

	// let uppercaseName; not required!

	$: uppercaseName = name.toUpperCase();

	$: console.log(name);

	$: if (name === "Alparslan") {
		console.log("It runs!");
		age = 31;
	}

	function incrementAge() {
		age += 1;
	}

	function changeName() {
		name = "Alparslan";
	}

	function nameInput(event) {
		const enteredValue = event.target.value;
		name = enteredValue;
	}
</script>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<!-- <input type="text" value={name} on:input={nameInput} /> -->
<input type="text" bind:value={name} />
<input type="text" bind:value={jobtitle} />
<textarea rows="3" type="text" bind:value={shortDescription} />

<ContactCard
	userName={name}
	jobTitle={jobtitle}
	{shortDescription}
	{userImage}
/>

<style>
	h1 {
		color: purple;
	}
</style>
