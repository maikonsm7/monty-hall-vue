<template>
<div class="door-area">
    <div class="door-frame" :class="{selected: selected && !open}"> <!-- aplica a class selected somente se a variavel selected e open forem verdadeiras -->
        <Presente v-if="open && hasPresente"/>
    </div>
  <div class="door" @click="selected = !selected" :class="{open}">
    <div class="numero">{{ num }}</div>
    <div class="maceneta" @click.stop="open = true"></div>
  </div>
  </div>
</template>

<script>
import Presente from './Presente.vue'

export default {
name: 'Porta',
components: {Presente},
props: {
    num: {},
    hasPresente: {type: Boolean}
},
data: function () {
    return {
        open: false,
        selected: false
    }
}
}
</script>

<style>
:root {
    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
}
.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #AAA;
    margin-bottom: 20px;
    font-size: 3rem;
    display: flex;
    justify-content: center;
}
.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;
    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);
    display: flex;
    justify-content: center;
    align-items: flex-end;
}
.door {
    position: absolute;
    top: 5px;
    height: 260px;
    width: 140px;
    background-color: chocolate;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}
.door .maceneta {
    height: 20px;
    width: 20px;
    border-radius: 10px;
    background-color: brown;
    align-self: flex-start;
    margin-top: 60px;
}
.door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}
.door.open {
    background-color: #0007;
}
.door.open .maceneta{
    display: none;
}
.door.open .numero{
    display: none;
}
</style>