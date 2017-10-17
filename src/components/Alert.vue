
<template>
<div>
    <!-- change to <div class="alert alert-danger" role="alert">  -->
    <div :class="updateAlert" role="alert">
        <slot name="info"></slot>
        <slot name="full"></slot>
    </div>
</div>
</template>

<script>
export default {
    props:['alert'],
    computed:{
      updateAlert(){
          if (this.alert) {
            return "alert alert-danger"
          } else {
            return "alert alert-primary"
          }
      }
    }
}
</script>

