<script>
import InputTag from './components/inputTag.vue'

export default{
  components:{
    InputTag
  },
  methods:{
    hanldeOnTagsChange(tags){
      console.log(tags)
    }
  }
}

</script>

<template>
  <!-- <InputTag :onTagsChange="hanldeOnTagsChange" /> -->
  <InputTag @onTagsChange="hanldeOnTagsChange" />
</template>

<style scoped>
</style>
