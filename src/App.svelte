<script>
  import Header from './UI/Header.svelte';
  import TextInput from './UI/TextInput.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte';
  import Button from './UI/Button.svelte';


  let meetups = [
    {
      id: 1,
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts to help you how to code',
      imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Caffe_Nero_coffee_bar%2C_High_St%2C_Sutton%2C_Surrey%2C_Greater_London.JPG/800px-Caffe_Nero_coffee_bar%2C_High_St%2C_Sutton%2C_Surrey%2C_Greater_London.JPG',
      address: '27th Nerd rood, 35224 New York',
      email: 'code@test.com'
    },
    {
      id: 2,
      title: 'Swim together',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts to help you how to code',
      imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Olympic_swimming_pool_%28Tbilisi%29.jpg/800px-Olympic_swimming_pool_%28Tbilisi%29.jpg',
      address: '27th Nerd rood, 35224 New York',
      email: 'code@test.com'
    }
  ];

  let title = "";
  let subtitle = "";
  let address = "";
  let imageUrl = "";
  let email = "";
  let description = "";

  function addMeetup(event){
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      address: address,
      imageUrl: imageUrl,
      email: email,
      description: description
    };

    meetups = [newMeetup,...meetups];
  }
</script>


<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header/>

<main>
  <form on:submit|preventDefault="{addMeetup}">
    <TextInput id="title" type="text" label="Title"       value={title} on:input={(event) => title = event.target.value } />  
    <TextInput id="subtitle" type="text" label="Subtitle" value={subtitle} on:input={(event) => subtitle = event.target.value } />  
    <TextInput id="address" type="text" label="Address"   value={address} on:input={(event) => address = event.target.value } />  
    <TextInput id="imageUrl" type="text" label="imageUrl" value={imageUrl} on:input={(event) => imageUrl = event.target.value } />  
    <TextInput id="email" type="email" label="Email"      value={email} on:input={(event) => email = event.target.value } />  
    <TextInput id="description" controlType="textarea" label="description" value={description} on:input={(event) => description = event.target.value } />  
    <Button type="submit" caption="Save"/>
  </form>
  <MeetupGrid {meetups}/>
</main>

