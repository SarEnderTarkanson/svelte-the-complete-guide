<script>
	import ContactCard from "./ContactCard.svelte";

	let userName = "";
	let age = 39;
	let jobTitle = "";
	let shortDescription = "";
	let userImage = "https://nyrami.com/assets/team/alpy.jpg";

	// let uppercaseName; not required!

	$: uppercaseName = userName.toUpperCase();

	$: console.log(userName);

	$: if (userName === "Alparslan") {
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
		userName = enteredValue;
	}
</script>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<!-- <input type="text" value={name} on:input={nameInput} /> -->
<input type="text" bind:value={userName} />
<input type="text" bind:value={jobTitle} />
<textarea rows="3" type="text" bind:value={shortDescription} />

<ContactCard {userName} {jobTitle} {shortDescription} {userImage} />

<style>
	h1 {
		color: purple;
	}
</style>
