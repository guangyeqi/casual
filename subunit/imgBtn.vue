<template>
    <div class="imgBtn" v-on:mouseenter="btnHover()" @mouseout="btnOut()" @mousedown="btnDown()" @click="btnClick">
        <!-- 图片 -->
        <img :src="src" alt="按钮" class="i_img" :status="status">
    </div>
</template>
<script>
    module.exports = {
        name: 'imgBtn',
        props: {
            src: String,
            name: String,
            type: {
                type: String,
                default: 'png'
            },
            canclick: {
                type: Boolean,
                default: true
            }
        },
        data() {
            return {
                status: 0,//按钮状态，0，normal。1，hover。2，keyDown。3，keyUp。
                src: '',//图片路径
                normal: '',
                hover: '',
                keyDown: '',
            }
        },
        methods: {
            btnHover() {
                if (this.$props.canclick) {
                    this.src = this.hover;
                    this.status = 2;
                }
            },
            btnOut() {
                if (this.$props.canclick) {

                    this.src = this.normal;
                    this.status = 1;
                }
            },
            btnDown() {
                if (this.$props.canclick) {

                    this.src = this.normal;
                    this.status = 3;
                }
            },
            btnClick() {
                let { name, canclick } = this.$props;
                if (canclick) {
                    this.$emit('onclick', name)
                }
            }
        },
        created() {
            let { src, name, type, canclick } = this.$props;
            if (canclick) {
                this.src = this.normal = src + name + '_1.' + type;
                this.hover = src + name + '_2.' + type;
                this.keyDown = src + name + '_3.' + type;
            } else {
                this.src = src + name + '_0.' + type;
                this.status = -1;
            }
        },
    }
</script>
<style scoped>
    .i_img {
        display: inline-block;
        width: 100%;
        height: 100%;
        overflow: hidden;
        pointer-events: none;
    }
</style>