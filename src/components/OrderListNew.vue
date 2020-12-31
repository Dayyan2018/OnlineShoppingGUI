<ul id="demo">
  <li v-repeat="items" class="item-{{$index}}">
    {{$index}} - {{parentMsg}} {{childMsg}}
  </li>
</ul>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/1.0.18/vue.min.js"></script>
<script>
// eslint-disable-next-line no-unused-vars
var demo = new Vue({
  el: '#demo',
  data: {
    parentMsg: 'Hello',
    items: [
      { childMsg: 'Foo' },
      { childMsg: 'Bar' }
    ]
  }
})
</script>