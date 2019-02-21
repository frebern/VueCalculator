<template>
    <button v-on:click="onClick">{{getText}}</button>
</template>

<script>

import Formula from "../js/formula.js"
import Command from "../js/command.js"

import LiteralFactory from "../js/type/literal/literal-factory.js"
import OperatorFactory from "../js/type/operator/operator-factory.js"
import CommandFactory from "../js/type/command/command-factory.js"

export default {
    name:"InputButton",
    data(){
        return {
            formula : Formula,
            command : Command,
            type    : this.$attrs["type"],
            value   : this.$attrs["value"],
            present : this.$attrs["present"]
        }
    },
    computed:{
        getText(){
            var value = this.value
            var present = this.present
            return present ? present : value
        },
        createInstance(){ //type에 따라 value object를 생성한다.
            console.log("getInstance()")
            var type = this.type
            var value = this.value
            if(!this.instance){
                if(OperatorFactory.isOperator(type)){
                    // plus, minus, multiply, divide
                    // 다른 연산 추가시 type/operator 에 해당 연산 추가하고 팩토리에 추가.
                    this.instance = OperatorFactory.create(value)
                } else if(CommandFactory.isCommandType(type)){
                    // equal, clear
                    // 다른 커맨드 추가시 type/command 에 해당 연산 추가하고 팩토리에 추가
                    this.instance = CommandFactory.create(value)
                } else if(LiteralFactory.isLiteralType(type)){
                    // 0~9, dot
                    this.instance = LiteralFactory.create(value)
                } else {
                    // 잘못된 분기!
                    alert("잘못된 호출입니다!")
                }
            }
            return this.instance
        }
    },
    methods:{
        // 각 버튼 클릭시, 버튼 타입에 따라 다르게 처리.
        onClick(){
            console.log("onClick : "+this.value)
            var type = this.type
            var value = this.value
            var formula = this.formula

            //num, op, dot 중 하나면 formula를 통해 수행
            if(formula.isFormulaType(type)){
                formula.insert(this.getInstance())
            } else if(command.isCommandType(type)){
                command.do(this.getInstance(), formula)
            } else {
                alert("부정한 버튼을 눌렀습니다.")
            }
        }
    }
}
</script>

<style>
button {
    font-size:18px;
    color:white;
    width:50px;
    line-height:160%;
    border:none;
    box-shadow: -1px 2px gray;
    margin:2px;
    background-color:#296ddb;
}
</style>
