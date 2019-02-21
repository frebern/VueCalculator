<template>
    <div id="output">
        <div id="formula">{{formula.convertToString()}}</div>
        <div id="result">{{calculator.calculate(formula)}}</div>
    </div>
</template>

<script>
import Formula from "../js/formula.js"
import Calculator from "../js/calculator.js"
export default {
    name:"OutputForm",
    data(){
        return {
            formula:Formula,
            calculator:Calculator
        }
    },
    created(){
        console.log("OutputForm")
        console.log(this.formula)
        console.log(this.calculator)
    }
}
</script>

<style>
#output{
    overflow:hidden;
    width:200px;
    height:32px;
    border: 1px solid black;
}
</style>
