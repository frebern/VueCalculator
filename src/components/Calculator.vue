<!-- 계산기 전체 폼 -->
<template>
  <div id="calculator">
    <OutputForm />
    <InputForm />
  </div>
</template>


<script>
import OutputForm from './OutputForm'
import InputForm from './InputForm'

export default {
  name: 'Calculator',
  components:{
    InputForm, OutputForm
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#calculator {
  margin:auto;
  width:250px;
  padding:10px;
  border: 3px solid gray;
  text-align:center;
}

</style>
