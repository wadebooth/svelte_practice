<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";
  import EditMeetup from "./Meetups/EditMeetup.svelte";

  let meetups = [
    {
      id: "m1",
      title: "GRUBBRR",
      subtitle: "Learn Svelte.js",
      description: "Today I will be working on a JS project using Svlete",
      imageURL:
        "https://1330878074.rsc.cdn77.org/wp-content/uploads/2021/06/GRUBBRR-Unveils-New-Modern-Interactive-Headquarters-in-Boca-Raton_-Florida.jpg",
      address: "1081 Holland Dr, Boca Raton, FL 33487",
      emailAddress: "wbooth@grubbrr.com",
      isFavorite: false,
    },
    {
      id: "m2",
      title: "Boca Code",
      subtitle: "Learn to code in ten weeks",
      description: "Build a final project with a frontend and backend",
      imageURL:
        "http://techhubsouthflorida.org/wp-content/uploads/2020/05/BocaCode-768x768.png",
      address: "7035 Beracasa Way #207, Boca Raton, FL 33433",
      contactEmail: "wademgmt@gmail.com",
      isFavorite: false,
    },
  ];

  let editMode;

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageURL: imageURL,
      contactEmail: email,
      address: address,
    };
    meetups = [...meetups, newMeetup];
  }

  function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = {
      ...meetups.find((m) => m.id === id),
    };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex((m) => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }
</script>

<Header />

<main>
  <Button caption="New Meetup" on:click={() => (editMode = "add")} />
  {#if editMode === "add"}
    <EditMeetup />
  {/if}
  <MeetupGrid {meetups} on:toggleFavorite={toggleFavorite} />
</main>

<style>
  main {
    margin-top: 5rem;
  }
</style>
