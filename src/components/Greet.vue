<template>
    <div>

        Hello From Prop, {{ name }}

    </div>
</template>

<script>
    export default {
        data(){
            return{

            }
        },
        props:['name']
    }
</script>

<style lang="scss" scoped>

</style>