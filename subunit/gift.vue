<template>
    <div class="gift">
        <!-- top -->
        <img src="img/12/top.png" alt="top" class="g_top">
        <!-- box -->
        <img src="img/12/box.png" alt="box" class="g_box">
        <!-- top -->
        <img src="img/12/bottom.png" alt="bottom" class="g_bottom">
    </div>
</template>
<script>
    module.exports = {
        name: 'imgBtn',
        props: {

        },
        data() {
            return {

            }
        },
        methods: {

        },
        created() {

        },
    }
</script>
<style lang="scss" scoped>
    .gift{
        position: fixed;
        top: 0;
        left: 0;
        z-index: 998;
        width: 100%;
        height: 100%;
        overflow: hidden;
        background: rgba(0,0,0,0.6);
    }
    .g_top{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        margin: 0 auto;
    }
</style>