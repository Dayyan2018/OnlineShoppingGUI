<template>
<div id = "orderinput">
  <h1>Enter your Order</h1>
  <form>
    <label for="Customer ID">Customer ID: </label>
    <input type="text" required>
  </form>
</div>
</template>


<script>
module.exports = {
data: function(){
   return {
     message: 'Hello you are on Custom page'
    }
  }
}
</script>

<style>
.submit-form {
  max-width: 100px;
  margin: auto;
}
</style>

