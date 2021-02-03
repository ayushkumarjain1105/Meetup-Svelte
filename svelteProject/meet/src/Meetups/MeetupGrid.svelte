<script>
    import MeetupItems from  './MeetupItems.svelte';
    export let meetups;
</script>
<style>
  section {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 1rem;
}

@media (min-width: 768px) {
  section {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>


<section id="meetups">
{#each meetups as meetup}
<MeetupItems
id={meetup.id}
title={meetup.title} 
subtitle={meetup.subtitle} 
imageUrl={meetup.imageUrl} 
description={meetup.description} 
address={meetup.address} 
email={meetup.contactEmail} 
addres={meetup.address}
isFav ={meetups.isFavorite}
on:togglefavorite/>
{/each}
</section>