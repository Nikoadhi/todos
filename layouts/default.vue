<template>
  <div>
    <b-container class="bv-example-row">
      <navbar></navbar>

  <b-row>
    <b-col><cardlist :data1="data1"></cardlist></b-col>
    
  </b-row>
</b-container>
    
  </div>
</template>

<script>
import Navbar from '../components/navbar'
import cardlist from '../components/cardlist'



export default {
  components: {
    Navbar,
    cardlist
  },
}
</script>

<style>
html {
  font-family: 'Source Sans Pro', 'Helvetica Neue', Arial, sans-serif;
}
</style>





<!-- 
1. Create input form
2. Store input
3. Create an array
4. Push input into array, completed=false