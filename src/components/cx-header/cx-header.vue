<template>
    <div class="container">
        <div class="content-wrapper">
            <div class="avatar">
                <img width="64" height="64" :src="seller.avatar" />
            </div>
            <div class="content">
                <div class="title">
                    <span class="brand"></span>
                    <span class="name">{{seller.name}}</span>
                </div>
                <div class="description">
                    {{seller.description}}/{{seller.deliveryTime}}分钟送达
                </div>
                <div v-if="seller.supports && seller.supports.length" class="support">
                    <small-icon :size=1 :type="seller.supports[0].type" />
                    <span class="text">{{seller.supports[0].description}}</span>
                </div>
            </div>
            <div v-if="seller.supports && seller.supports.length" class="support-count">
                <span class="count">{{seller.supports.length}}个</span>
                <i class="icon-keyboard_arrow_right"></i>
            </div>
        </div>
        <div class="bulletin-wrapper">
            <span class="bulletin-title"></span>
            <span class="bulletin-text">{{seller.bulletin}}</span>
            <i class="icon-keyboard_arrow_right"></i>
        </div>
        <div class="background-wrapper">
            <img width="100%" height="100%" :src="seller.avatar" />
        </div>
    </div>
</template>

<script>
import SmallIcon from 'components/small-icon/small-icon'
export default {
    props: {
        seller: {
            type: Object,
            default: () => {}
        }
    },
    components: {
        SmallIcon
    }
}
</script>

<style lang="stylus" scoped>
    @import "~common/stylus/mixin"
    @import "~common/stylus/variable"
    .container
        position relative
        overflow hidden
        color: $color-white
        background: $color-background-ss
        .content-wrapper
            position relative
            display flex
            align-items center
            padding 24px 12px 18px 24px
            .avatar
                margin-right 16px
                img
                    border-radius 2px
            .content
                flex 1
                .title
                    display flex
                    align-items center
                    margin-bottom 8px
                    .brand
                        width 30px
                        height 18px
                        bg-image('./images/brand')
                        background-size: 30px 18px
                        background-repeat: no-repeat
                    .name
                        margin-left: 6px
                        font-size: $fontsize-large
                        font-weight: bold
                .description
                    margin-bottom: 8px
                    font-size: $fontsize-small
                .support
                    display: flex
                    align-items: center
                    .support-ico
                        margin-right: 4px
                    .text
                        font-size: $fontsize-small-s
            .support-count
                position absolute
                right 12px
                bottom 14px
                display flex
                align-items center
                padding 0 8px
                height 24px
                line-height 24px
                text-align center
                border-radius 14px
                background: $color-background-sss
                .count
                    font-size: $fontsize-small-s
                .icon-keyboard_arrow_right
                    margin-left: 2px
                    // line-height: 24px
                    font-size: $fontsize-small-s
        .bulletin-wrapper
            display flex
            align-items center
            height 28px
            line-height: 28px
            padding: 0 8px
            background: $color-background-sss
            .bulletin-title
                width: 22px
                height: 12px
                margin-right: 4px
                bg-image('./images/bulletin')
                background-size: 22px 12px
                background-repeat: no-repeat
            .bulletin-text
                flex: 1
                white-space: nowrap
                overflow: hidden
                text-overflow: ellipsis
                font-size: $fontsize-small-s
            .icon-keyboard_arrow_right
                width: 10px
                font-size: $fontsize-small-s
        .background-wrapper
            position absolute
            top 0
            left 0
            width 100%
            height 100%
            z-index -1
            filter blur(10px)
</style>