<template>
    <div>
        <div>This is a Popup</div>
        <button @click="$emit('close')">Close Popup</button>
    </div>
</template>

<script>
    export default {
        name:'popup',
        emits:['close']
    }
</script>

<style lang="scss" scoped>

</style>