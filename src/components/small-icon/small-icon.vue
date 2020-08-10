<template>
    <span class="small-icon" :class="iconStyl"></span>
</template>

<script>
export default {
    name: "small-icon",
    props: {
        size: {
            type: Number
        },
        type: {
            type: Number
        }
    },
    computed: {
        iconStyl() {
            const classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
            return `icon-${this.size} ${classMap[this.type]}`
        }
    }
}
</script>

<style lang="stylus" scoped>
    @import "~common/stylus/mixin"
    .small-icon
        display inline-block
        background-repeat no-repeat
    .icon-1
        width 12px
        height 12px
        background-size 12px 12px
        &.decrease
            bg-image('./images/decrease_1')
        &.discount
            bg-image('./images/discount_1')
        &.special
            bg-image('./images/special_1')
        &.invoice
            bg-image('./images/invoice_1')
        &.guarantee
            bg-image('./images/guarantee_1')
    .icon-2
        width 16px
        height 16px
        background-size 16px 16px
        &.decrease
            bg-image('./images/decrease_2')
        &.discount
            bg-image('./images/discount_2')
        &.special
            bg-image('./images/special_2')
        &.invoice
            bg-image('./images/invoice_2')
        &.guarantee
            bg-image('./images/guarantee_2')
    .icon-3
        width 12px
        height 12px
        background-size 12px 12px
        &.decrease
            bg-image('./images/decrease_3')
        &.discount
            bg-image('./images/discount_3')
        &.special
            bg-image('./images/special_3')
        &.invoice
            bg-image('./images/invoice_3')
        &.guarantee
            bg-image('./images/guarantee_3')
    .icon-4
        width 16px
        height 16px
        background-size 16px 16px
        &.decrease
            bg-image('./images/decrease_4')
        &.discount
            bg-image('./images/discount_4')
        &.special
            bg-image('./images/special_4')
        &.invoice
            bg-image('./images/invoice_4')
        &.guarantee
            bg-image('./images/guarantee_4')
</style>