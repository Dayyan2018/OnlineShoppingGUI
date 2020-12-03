<template>
    
  <!-- some code condensed for display reasons -->
  <FormulateForm v-model="values" @submit="submitHandler">
  <FormulateInput name="custid" type="textarea" label="Customer" v-model="custid" />
    <h2>Online Grocery</h2>
    <FormulateInput
      type="group"
      name="orders"
      label="Create your custom grocery order"
      help="Choose your grocery items"
      add-label="+ Add Order"
      validation="required"
      :repeatable="true"
    >
      <div class="order">
        <FormulateInput name="customer" label="Customer Name" type="textarea" />
        <FormulateInput name="product" type="select" label="Grocery Items" validation="required" :options="{ beer: 'Beer', butter: 'Butter', eggs: 'Eggs', milk: 'Milk'}" />
        <FormulateInput name="qty" label="Quantity" type="number" min="1" validation="required|min:1" />
      </div>
    </FormulateInput>

    <FormulateInput name="deliveryMethod" type="radio" label="Delivery Method" validation="required" :options="{ local: 'Local Pick-up', delivery: 'Delivery (5-mile radius)' }" />
    <FormulateInput name="orderNotes" type="textarea" label="Order Notes" help="Allergies? Delivery instructions? Don't need the spoons? Let us know!" />
    <FormulateInput type="submit" value="Place Order" />
    <pre>{{ values }}</pre>
  </FormulateForm>
</template>
<script>
import OrderDataService from "../services/OrderDataService";

/*export default { data () { return { values: {} } }, methods: {submitHandler () { alert(`Thank you for your order!`) } } }*/
export default {
  data () {
    return {
     values: {}
      
    }
  },
  methods: {
    submitHandler() {
      //alert(`Thank you for your order!`)
      var data = {
        custid: this.values.custid,
        info:this.values,
        dot: new Date()
      };
      OrderDataService.create(data)
      alert(`Thank you for your order!`)
      console.log(data)
      
    }
  }

}

</script>








