<script>
	let name="Alpy";
	let age=39;

	function incrementAge(){
		age +=1;
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name} and my age is {age}!</h1>
<button on:click="{incrementAge}">Change age</button>
