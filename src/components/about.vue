<template>
  <div class="card">
    <!--<img class="card-img-top" src="https://tindir.github.io/images/avatar.png" alt="Card image cap">-->
    <div class="card-body">
      <h5 class="card-title">{{fio}}</h5>
    </div>
    <ul class="list-group list-group-flush">
      <li class="list-group-item">
        <i class="fa fa-briefcase"></i>
        {{position}}
      </li>
      <li class="list-group-item">
        <i class="fa fa-home"></i>
        {{address}}
      </li>
      <li class="list-group-item">
        <i class="fa fa-envelope"></i>
        {{contact}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name:'about',  
  props: ['fio', 'position', 'address', 'contact'], 
  data: function() {
    return {
    };
  }
}
</script>

<style>

</style>