<template>
    <div>
        <my-top/>
        <house-ship/>
        <my-footer/>
    </div>
</template>

<script>
    import MyFooter from '~/components/Footer.vue'
    import MyTop from '../components/top'
    import houseShip from '~/components/houseShip.vue'
    export default {
        components:{
            MyFooter,MyTop,houseShip
        },
        name: "tool"
    }
</script>

<style scoped lang="less">

</style>