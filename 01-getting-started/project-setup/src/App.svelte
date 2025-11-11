<script>
	let name = "Alpy";
	let age = 39;

	$: uppercaseName = name.toUpperCase();

	$: console.log(name);

	$: if (name === "Alparslan") {
		age = 19;
	}

	function incrementAge() {
		age += 1;
	}

	function changeName() {
		name = "Alparslan";
		age = 19;
	}
</script>

<h1>Hello {uppercaseName} and my age is {age}!</h1>
<button on:click={incrementAge}>change age</button>
<button on:click={changeName}>change name</button>

<style>
	h1 {
		color: purple;
	}
</style>
