<template>
    <div :class="{'vux-1px-b': showBorder}"
         class="z-header zflex">
        <span class="z-header-left zflex zflex1">
                        <div class="z-arrow zflex" :style="{color: arrowColor}" @click="goback(url)">
                            <svg class="zicon zheader-icon" aria-hidden="true" v-show="showArrow">
                                <use xlink:href="#icon-fanhui"></use>
                            </svg>
                             <span class="leftwords" v-show="showBack">{{backWords}}</span>
    </div>
    <slot name="leftitems"></slot>
    </span>
    <span class="z-header-middle">{{title}}
            <slot name="middleitems" v-if="!title"></slot>
        </span>
    <span class="z-header-right zflex zflex1">
                <slot name="rightitems"></slot>
            </span>
    </div>
</template>

<style lang="less">
@import '../../assets/styles/setArrow.less';
.setTapColor(@c: rgba(0, 0, 0, 0)) {
    -webkit-tap-highlight-color: @c;
}

.z-arrow {
    height: 0.5rem;
    .setTapColor();
    .leftwords {
        font-size: 15px;
        color: #ccc;
    }
}

.z-header {
    line-height: 1.4;
    font-size: 19px;
    height: 0.85rem;
    text-align: center; 
    padding: 0.08rem 0.2rem;
    // padding: 25px 0.2rem 0.1rem;
    box-sizing: border-box; //background: rgba(0, 0, 0, 0);
    background: #fff;
    position: absolute;
    width: 100%;
    top: 0;
    z-index: 100;
    left: 0;
    transition: all ease 0.3s;
    &.vux-1px-b {
        position: absolute;
    }
}

.z-header-left {
    // text-align: left;
    position: relative;
}

.z-header-right {
    // text-align: right;
    justify-content: flex-end;
}

.zheader-icon {
    font-size: 0.4rem;
}

.z-header-middle {
    width: 3.8rem;
}

.zheader-icon-word {
    font-size: 12px;
}
</style>
<script>
export default {
    name: 'z-header',
    props: {
        showBorder: {
            type: Boolean,
            default: true
        },
        title: {
            type: String,
            // default: '主页'
        },
        showBack: {
            type: Boolean,
            default: false
        },
        showArrow: {
            type: Boolean,
            default: true
        },
        arrowColor: {
            type: String,
            default: '#e74037'
        },
        backWords: {
            type: String,
            default: '返回'
        },
        url: {
            type: String
        }
    },
    methods: {
        goback(url) {
            if (this.$route && url) {
                this.$router.push(url)
            } else if (this.$route && 　!url) {
                this.$router.go(-1)
            } else if (!this.$route && url) {
                location.href = '#/' + url
            } else {
                historu.go(-1)
            }
            this.$emit('goback')
        }
    }

}
</script>