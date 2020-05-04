<template>
  <div class="col mb-4">
    <div id="eskill" class="card h-100">
      <div class="card-body">
        <ul class="list-group list-group-flush">
          <li class="list-group-item">
            <div class="work-exp">
              <h3 class>{{data.item}}</h3>
              <span v-html="data.comment"></span>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "eskill",

  props: ["data"],

  data: function() {
    return {};
  }
};
</script>

<style>
.card {
  margin-top: 1em;
}
</style>