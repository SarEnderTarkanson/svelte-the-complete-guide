<script>
	let name="Alpy";
	let age=39;

	$:uppercaseName = name.toUpperCase();

	function incrementAge(){
		age +=1;
	}

	function changeName(){
		name = "Alparslan";
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName} and my age is {age}!</h1>
<button on:click="{incrementAge}">change age</button>
<button on:click="{changeName}">change name</button>
