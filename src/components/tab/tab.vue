<template>
    <div class="tab">
        <cube-tab-bar
            ref="tabBar"
            v-model="selectedLabel"
            :data="tabsList"
            :useTransition=false
            :showSlider=true>
        </cube-tab-bar>
        <div class="slide-wrapper">
            <cube-slide
                :loop="false"
                :auto-play="false"
                :show-dots="false"
                :options="slideOptions"
                :initial-index="index"
                ref="slide"
                @scroll="handleScroll"
                @change="handleChange">
                <cube-slide-item v-for="(tab,index) in tabsList" :key="index">
                    <component :is="tab.component" :data="tab.data" ref="component"></component>
                </cube-slide-item>
            </cube-slide>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            index: this.initialIndex,
            slideOptions: {
                listenScroll: true,
                probeType: 3,
                directionLockThreshold: 0
            }
        }
    },
    props: {
        tabsList: {
            type: Array,
            default: () => []
        },
        initialIndex: {
            type: Number,
            default: 0
        }
    },
    computed: {
        selectedLabel: {
            get() {
                return this.tabsList[this.index].label
            },
            set(newValue) {
                this.index = this.tabsList.findIndex(item => {
                    return newValue === item.label
                })
            }
        }
    },
    mounted() {
        this.handleChange(this.index)
    },
    methods: {
        handleScroll(pos) {
            const tabBarWidth = this.$refs.tabBar.$el.clientWidth
            const slideWidth = this.$refs.slide.slide.scrollerWidth
            const transform = -pos.x / slideWidth * tabBarWidth
            this.$refs.tabBar.setSliderTransform(transform)
        },
        handleChange(current) {
            this.index = current;
            const component = this.$refs.component[current]
            component.fetch && component.fetch()
        }
    }
}
</script>

<style lang="stylus" scoped>
    @import '~common/stylus/variable';
        .tab
            display flex
            flex-direction column
            height 100%
            >>> .cube-tab
                padding 10px 0
            .slide-wrapper
                flex 1
                overflow hidden
</style>