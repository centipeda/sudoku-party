<template>
    <div class="box" :class="{focused: focus}">
        <p>{{ number }}</p>
    </div>
</template>

<script>
export default {
    props: ['number', 'row', 'column', 'focus'],
}
</script>

<style>
.box {
    height: 50px;
    overflow: hidden;
}
.box.focused {
    background-color: #ffaca6;
}
p {
    font-size: 24pt;
    line-height: 50px;
    margin: 0;
    user-select: none;
    color: black;
}
</style>