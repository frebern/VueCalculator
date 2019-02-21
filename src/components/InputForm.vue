<template>
    <div>
        <div>
            <InputButton type="num" value=1 />
            <InputButton type="num" value=2 />
            <InputButton type="num" value=3 />
            <InputButton type="op"  value="plus" present="+" />
        </div>
        <div>
            <InputButton type="num" value=4 />
            <InputButton type="num" value=5 />
            <InputButton type="num" value=6 />
            <InputButton type="op"  value="minus" present="-" />
        </div>
        <div>
            <InputButton type="num" value=7 /> 
            <InputButton type="num" value=8 />
            <InputButton type="num" value=9 />
            <InputButton type="op"  value="multiply" present="×" />
        </div>
        <div>
            <InputButton type="dot"  value="dot" present="." />
            <InputButton type="num"  value=0 />
            <InputButton type="comm" value="equal" present="=" />
            <InputButton type="op"   value="divide" present="÷" />
        </div>
        <div class="full">
            <InputButton type="comm" value="clear" present="Clear All" />
        </div>
    </div>
</template>

<script>

import InputButton from "./InputButton"

export default {
    name : "InputForm",
    components:{InputButton}
}
</script>

<style scoped>
</style>
