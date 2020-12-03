<template>

  <div class="list row">
    <div class="col-md-8">
      <div class="input-group mb-3">
        <input type="text" class="form-control" placeholder="Search by Order"
          v-model="orders.custid"/>
        <div class="input-group-append">
          <button class="btn btn-outline-secondary" type="button"
            @click="searchTitle"
          >
            Search
          </button>
        </div>
      </div>
    </div>
    <div class="col-md-6">
      <h4>Orders List</h4>
      <ul class="list-group">
        <li class="list-group-item"
          :class="{ active: index == currentIndex }"
          v-for="(order, index) in orders"
          :key="index"
          @click="setActiveOrder(order, index)"
        >
          {{ orders }}
        </li>
      </ul>

      
      <button class="m-3 btn btn-sm btn-danger" @click="removeAllOrders">
        Remove All
      </button>
    </div>
        <div class="col-md-6">
      <div v-if="currentOrder">
        <h4>Order</h4>
        <div>
          <label><strong>Id:</strong></label> {{ currentOrder.id }}
        </div>
        <div>
          <label><strong>CustomerID:</strong></label> {{ orders.custid }}
        </div>
      

        <a class="badge badge-warning"
          :href="'/orders/' + currentOrder.id"
        >
          Edit
        </a>
      </div>
      <div v-else>
        <br />
        <p>Please click on a Order...</p>
      </div>
    </div>
  </div>
</template>

<script>
import OrderDataService from "../services/OrderDataService";
//this.orders = 'No Order' ;
export default {
  name: "order-list",
  data() {
    return {
      orders: [],
      currentOrder: null,
      currentIndex: -1,
      id: ""
    };
  },
  methods: {
    retrieveOrders() {
      OrderDataService.getAll()
        /*.then(response => {this.orders = response.data.id;console.log(response.data); })*/
         .then((response)=>(this.orders.custid = response.data.custid))
         /*console.log(this.orders.custid)*/
          
        .catch(e => {
          console.log(e);
        });
    },

    refreshList() {
      this.retrieveOrders();
      this.currentOrder = null;
      this.currentIndex = -1;
    },

    setActiveOrder(order, index) {
      this.currentOrder = order;
      this.currentIndex = index;
    },

    removeAllOrders() {
      OrderDataService.deleteAll()
        .then(response => {
          console.log(response.data);
          this.refreshList();
        })
        .catch(e => {
          console.log(e);
        });
    },
    
    searchTitle() {
      OrderDataService.findById('MAX25')
        .then(response => {
          this.orders = response.data;
          console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        });
    }
  },
  mounted() {
    this.retrieveOrders();
  }
};
</script>

<style>
.list {
  text-align: left;
  max-width: 750px;
  margin: auto;
}
</style>
