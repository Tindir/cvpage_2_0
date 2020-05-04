<template>
  <div id="education" class="education">
    <div class="card">
      <div class="card-body">
        <ul class="list-group list-group-flush">
          <li class="list-group-item">
            <div class="work-exp">
              <h3 class>{{data.institution}}</h3>
              <h6 class="w3-text-teal">
                <i class="fa fa-calendar"></i>
                {{data.periodS}} - {{data.periodE}}
              </h6>
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
  name: "education",

  props: ["data"],

  data: function() {
    return {};
  }
};
</script>

<style>
.card{
        margin-top: 1em
    }
</style>