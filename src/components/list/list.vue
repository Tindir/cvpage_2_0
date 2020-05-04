<template>
<div calss="list-container">  
  
 <div class="card">
    <div class="card-header bg-light">
      <slot name="ListHeader"></slot>
    </div>
 </div>

  <slot name="ListBody"></slot>

  <slot name="ListFooter"></slot>

</div> 
</template>

<script>

export default {
  name: "list",
  props: ["templateName", "data"], 
  components: { 
    
  },
 
  data: function() {
    return {
        
      };
    },
  computed: {
      
  },

  methods: {
    
  }
}
</script>
  
<style>
  .list-container{margin-bottom: 1em;}
</style>