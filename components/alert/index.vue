<template>
  <div class="mb-4 rounded-lg px-6 py-5 text-base" :class="color" v-text="list.name">
    
  </div>
</template>

<script>
export default {
  props: {
    list: {
      type: Object,
      required: true
    }
  },
  computed: {
    color() {
        if(this.list.status == 'done'){
            return 'bg-green-100 text-green-700';
        }else{
            return 'bg-yellow-100 text-yellow-700'
        }
    },
  }
}
</script>
