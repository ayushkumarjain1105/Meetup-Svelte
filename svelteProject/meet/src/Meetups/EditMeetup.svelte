<script>
  import {createEventDispatcher} from 'svelte';
  import TextInput from '../UI/TextInput.svelte';
  import Button from '../UI/Button.svelte';
  import Modal from '../UI/Modal.svelte';
  
  let title ='';
	let subtitle='';
	let address='';
	let imageURL='';
	let email='';
  let description='';
  
  const dispatch = createEventDispatcher();

  function submitForm() {
    dispatch('save',{
      title:title,
      subtitle:subtitle,
      address:address,
      imageURL:imageURL,
      description:description,
      email:email
    });
  }
  function cancel(){
      dispatch('cancel');
  }
</script>
<style>
  	form{
		width: 100%;
	
	}
</style>


<Modal title="Edit Meetup Data" on:cancel>
<form on:submit|preventDefault="{submitForm}">
  <TextInput 
   id="title"
   label="Title" 
   value={title} 
   
   on:input="{(event) =>title = event.target.value}"/>
   <TextInput 
   id="subtitle"
   label="Subtitle" 

   value={subtitle} 
   on:input="{(event) =>subtitle = event.target.value}"/>
   <TextInput 
    id="address"
    label="Address" 
    
    value={address} 
    on:input="{(event) =>address = event.target.value}"/>
    <TextInput 
    id="imageURL"
    label="Image URL"
  
    value={imageURL} 
    on:input="{(event) =>imageURL = event.target.value}"/>
    <TextInput 
    id="email"
    label="E-Mail" 
    type="email"
    value={email} 
    on:input="{(event) =>email = event.target.value}"/>
    <TextInput 
    id="decription"
    label="Decription"
    controlType="textarea"
    value={description} 
    on:input="{(event) =>description = event.target.value}"/>
</form>
<div slot="footer">
  <Button type="button" mode="outline" on:click={submitForm} >Save</Button>
  <Button type="button" on:click={cancel} >Cancel</Button>
</div>
</Modal>