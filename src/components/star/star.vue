<template>
    <div class="star-container" :class="starType">
        <span class="star-item" :class="item" v-for="(item, index) in starList" :key="index"></span>
    </div>
</template>

<script>
const LENGTH = 5;
const CLS_ON = 'on';
const CLS_HALF = 'half';
const CLS_OFF = 'off';

export default {
    props: {
        score: {
            type: Number,
        },
        size: {
            type: Number
        }
    },
    computed: {
        starType() {
            return `star-${this.size}`
        },
        starList() {
            const result = []
            // 处理尾数不为0.5的分数，向下取整。转成尾数为0或0.5的分数
            const score = Math.floor(this.score * 2) / 2
            // 如果true，则分数就是整数，反之是小数
            const hasInteger = (score % 1) === 0
            let resultNum = hasInteger ? score : Math.floor(score)
            for(let i = 0; i < resultNum; i++) {
                result.push(CLS_ON)
            }
            if(!hasInteger) {
                result.push(CLS_HALF)
            }
            while(result.length < LENGTH) {
                result.push(CLS_OFF)
            }
            return result
        }
    }
}
</script>

<style lang="stylus" scoped>
    @import '~common/stylus/mixin';
    .star-container
        display flex
        align-items center
        justify-content center
        .star-item
            display inline-block
            background-repeat no-repeat
        &.star-24
            .star-item
                width 10px
                height 10px
                margin-right 3px
                background-size 10px 10px
            &.last-child
                margin-right 0
            .on
                bg-image('./images/star24_on')
            .half
                bg-image('./images/star24_half')
            .off
                bg-image('./images/star24_off')
        &.star-36
            .star-item
                width 15px
                height 15px
                margin-right 6px
                background-size 15px 15px
            &:last-child
                margin-right 0
            .on
                bg-image('./images/star36_on')
            .half
                bg-image('./images/star36_half')
            .off
                bg-image('./images/star36_off')
        &.star-48
            .star-item
                width 20px
                height 20px
                margin-right 22px
                background-size 20px 20px
            &:last-child
                margin-right 0
            .on
                bg-image('./images/star48_on')
            .half
                bg-image('./images/star48_half')
            .off
                bg-image('./images/star48_off')
</style>