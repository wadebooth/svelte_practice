<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";

  let title = "";
  let subtitle = "";
  let email = "";
  let imageURL = "";
  let description = "";
  let address = "";

  const dispatch = createEventDispatcher();

  function submitForm() {
    dispatch("save", {
      title: title,
      subtitle: subtitle,
      address: address,
      email: email,
      description: description,
      imageURL: imageURL,
    });
  }
</script>

<form
  on:submit|preventDefault={() => {
    dispatch("save");
  }}
>
  <TextInput
    id="title"
    label="Title"
    type="text"
    value={title}
    on:input={(event) => (title = event.target.value)}
  />
  <TextInput
    id="subtitle"
    label="Subtitle"
    type="text"
    value={subtitle}
    on:input={(event) => (subtitle = event.target.value)}
  />
  <TextInput
    id="address"
    label="Address"
    type="text"
    value={address}
    on:input={(event) => (address = event.target.value)}
  />
  <TextInput
    id="imageUrl"
    label="Image URL"
    type="text"
    value={imageURL}
    on:input={(event) => (imageURL = event.target.value)}
  />
  <TextInput
    id="email"
    label="E-Mail"
    type="email"
    value={email}
    on:input={(event) => (email = event.target.value)}
  />
  <TextInput
    id="description"
    label="Description"
    controlType="textarea"
    value={description}
    on:input={(event) => (description = event.target.value)}
  />
  <Button type="submit" caption="Save" />
</form>

<style>
  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>
