<script>
  let enteredPassword = "";
  let passwordVailidity = "short";
  let passwords = [];
  $: if (enteredPassword.trim().length < 5) {
    passwordVailidity = "short";
  } else if (enteredPassword.trim().length > 10) {
    passwordVailidity = "long";
  } else {
    passwordVailidity = "valid";
  }

  function confirmPassword() {
    if (passwordVailidity === "valid") {
      passwords = [...passwords, enteredPassword];
      enteredPassword = "";
    }
  }

  function removePassword(index) {
    passwords = passwords.filter((pw, idx) => {
      return idx !== index;
    });
  }
</script>

<main>
  <input type="password" bind:value={enteredPassword} />

  <button on:click={confirmPassword}>Confirm Password</button>
  {#if passwordVailidity === "short"}
    <p>Password is too short</p>
  {:else if passwordVailidity === "long"}
    <p>Password is too long</p>
  {:else}
    <p>Password {enteredPassword}</p>
  {/if}

  <ul>
    {#each passwords as pw, i}
      <!-- svelte-ignore a11y_click_events_have_key_events -->
      <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
      <li on:click={removePassword.bind(this, i)}>{pw}</li>
    {/each}
  </ul>
</main>

<style>
</style>
