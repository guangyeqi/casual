<template>
    <div :style="style" @mouseenter="btnEnter()" @mouseout="btnOut()" @mousedown="btnDown()" @click="btnClick"></div>
</template>
<script>
    module.exports = {
        name: 'imgBtn',
        props: {
            src: String,
            name: String,
            height:Number
        },
        data() {
            return {
                status: 0,//按钮状态，1，normal。2，hover。3，keyDown。3。
                style: {
                    background: '',
                },
                normal: '',
                hover: '',
                keyDown: ''
            }
        },
        methods: {
            btnEnter() {
                this.style.background = this.hover;
                this.status = 2;
            },
            btnOut() {
                this.style.background = this.normal;
                this.status = 1;
            },
            btnDown() {
                this.style.background = this.normal;
                this.status = 3;
            },
            btnClick() {
                this.$emit('onclick', name)
            }
        },
        created() {
            let { src,height } = this.$props;
            this.style.background = this.normal = 'url(' + src + ') no-repeat 0 0';
            this.hover = this.normal = 'url(' + src + ') no-repeat 0 -'+height+'px';
            this.keyDown = this.normal = 'url(' + src + ') no-repeat 0 -'+(height*2)+'px';
        },
    }
</script>