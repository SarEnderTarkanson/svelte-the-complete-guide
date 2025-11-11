<script>
	import ContactCard from "./ContactCard.svelte";

	let name = "Alpy";
	let age = 30;

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

<ContactCard userName="{name}"/>

<style>
	h1 {
		color: purple;
	}
</style>
