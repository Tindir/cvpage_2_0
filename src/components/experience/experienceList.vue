<template>
<div class="list-container">  
  <div class="card">
    <div class="card-header bg-light">
      <i class="fas fa-archive"></i> Опыт работы
    </div>
  </div>
    <div v-for="item in exp" v-bind:key="item.id">
      <experience :item="item"/>
    </div>
</div>  
</template>

<script>
import experience from "./expirience.vue";
import experienceInfo from "@/assets/experience.json";

export default {
  name: "experienceList",
 
 components: { 
    experience    
  },
 
 data: function() {
      return {
       exp: this.getExperienceInfo()

      };
    },

methods: {

    getExperienceInfo: function() {
     var out = experienceInfo;
      return out
    }

  }
}
</script>

<style scoped>
  .list-container{margin-bottom: 1em;}
</style>>
