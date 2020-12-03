<template>
<div class= "order-form">
  <div class = "form-group" width=200px>
  <label for="custid">Customer Code</label>
    <input type = "text" class = "form-control" id= "customerid" vmodel = "order.custid" name="custid" width=200px/>
  </div>

  <div class = "form-group" width=300px>
  <label for="info">Order Details</label>
    <input type = "text" class = "form-control" id= "orderinfo" vmodel = "order.info" name="info" width=300px/>
  </div>
  <button @click="saveOrder" class="btn btn-success">Place Order</button>
</div>
</template>




<script>
import OrderDataService from "../services/OrderDataService";

module.exports = {
  name: "add-order",
  data() {
    return {
      order: {
        id: null,
        custid: "",
        info: ""
      },
      submitted: true
    };
  },
    methods: {
    saveOrder() {
      var data = {
        custid: this.order.custid,
        info: this.order.info
      };

      OrderDataService.create(data)
        .then(response => {
          this.order.id = response.data.id;
          console.log(response.data);
          this.submitted = true;
        })
        .catch(e => {
          console.log(e);
        });
    },
    
    newOrder() {
      this.submitted = false;
      this.order = {};
    }
  }
};
</script>

<style>
.order-form {
 max-width: 400px;
 margin: auto;
}
</style>

