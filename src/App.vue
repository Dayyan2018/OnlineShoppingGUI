
<template>
  <div id="app">
    <nav class="navbar navbar-expand navbar-warning bg-warning">
      <a href="#" class="navbar-brand">RizCoder</a>
      <div class="navbar-nav mr-auto">
        <li class="nav-item">
          <a href="/Orders" class="nav-link">Orders</a>
        </li>
        <li class="nav-item">
          <a href="/add" class="nav-link">Add</a>
        </li>
        <li class="nav-item">
          <a href="/new" class="nav-link">New</a>
        </li>
      </div>
    </nav>

    <div class="container mt-3">
      <router-view />
    </div>
  </div>
</template>

<script>
export default {
  name: "app"
};
</script>
