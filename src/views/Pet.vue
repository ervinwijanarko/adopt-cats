<template>
  <div class="about">
    {{ $route.params.species}}
    {{ $route.params.id}}
  </div>
</template>
<script>
import { mapState } from 'vuex'

export default {
    data(){
        return {
             
        }
    },

    computed: {
        ...mapState([
            'cats',
            'dogs'
        ])
    } 

    
}
</script>