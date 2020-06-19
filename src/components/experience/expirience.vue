<template>
  <div id="expirience" class="expirience">
    <div class="card">
      <div class="card-body">
        <ul class="list-group list-group-flush">
          <li class="list-group-item">
            <div class="work-exp">
               <h3 class>{{data.position}}</h3>
            <h6 class="w3-text-teal">
              <i class="fa fa-calendar"></i>
              {{data.s_period}} - {{data.e_period}}
            </h6>
            <p class='header'><span>Обязанности:</span></p>
            <span v-html="data.responsibility"></span>
            <p class='header'><span>Достижения:</span></p>
            <span v-html="data.progress"></span>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "experience",
  props: ["data"],
  data: function() {
    return {};
  }
};
</script>

<style scoped>
P {
  margin: 0em;
}
.card {
  margin-top: 1em;
}
.header{
  margin-top: 1em;
  margin-bottom: 1em;
}

</style>