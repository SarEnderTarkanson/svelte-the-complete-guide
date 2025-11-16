<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Alpy";
  let title = "Software Engineer";
  let image = "https://avatars.githubusercontent.com/u/80176136?v=4";
  let description = "";
  let formState = "empty";

  let createdContacts = [];

  function addContactCard() {
    if (
      name.trim().length === 0 ||
      title.trim().length === 0 ||
      image.trim().length === 0 ||
      description.trim().length === 0
    ) {
      formState = "invalid";
      return;
    }
    createdContacts = [
      ...createdContacts,
      {
        name: name,
        jobTitle: title,
        userImage: image,
        description: description,
      },
    ];
    formState = "done";
  }
</script>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc"></textarea>
  </div>
</div>

<button on:click={addContactCard}>Add Contact Card</button>

{#if formState === "invalid"}
  <p style="color: red;">Invalid input.</p>
{:else}
  <p style="color: red;">Please enter some data and then hit the button!</p>
{/if}
{#each createdContacts as createdContact, i}
  <h2># {i}</h2>
  <ContactCard
    userName={createdContact.name}
    jobTitle={createdContact.jobTitle}
    description={createdContact.description}
    userImage={createdContact.userImage}
  />
{:else}
  <p>Please start adding some contacts, we found none!</p>
{/each}

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>
