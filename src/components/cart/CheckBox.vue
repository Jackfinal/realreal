<template>
    <div class="z-checkbox zflex"
         v-if="position && position == 'right'">
        <div class="checkbox-miidle zflex1">
            <slot></slot>
        </div>
        <label :for="id"
               class="check-label zflex">
            <input v-if="type && type =='radio'"
                   type="radio"
                   class="z-check"
                   name="checkit"
                   :value="id"
                   :checked="checked"
                   :id="id"
                   @change="change(value)">
            <input v-else
                   type="checkbox"
                   class="z-check"
                   name="checkit"
                   :value="id"
                   :checked="checked"
                   :id="id"
                   @change="change(value)">
            <icon icon="icon-yuanxingxuanzhongfill"
                  class="boxcheck red"></icon>
            <icon icon="icon-yuanxingweixuanzhong"
                  class="boxnocheck red"></icon>
        </label>
    </div>
    <div class="z-checkbox zflex" v-else>
    
        <label :for="id"
               class="check-label zflex">
            <input v-if="type && type =='radio'"
                   type="radio"
                   class="z-check"
                   name="checkit"
                   :value="id"
                   :checked="checked"
                   :id="id"
                   @change="change(value)">
            <input v-else
                   type="checkbox"
                   class="z-check"
                   name="checkit"
                   :value="id"
                   :checked='checked'
                   :id="id"
                   @change="change(value)">
            <icon icon="icon-yuanxingxuanzhongfill"
                  class="boxcheck red"></icon>
            <icon icon="icon-yuanxingweixuanzhong"
                  class="boxnocheck red"></icon>
        </label>
        <div class="checkbox-miidle zflex1">
            <slot name="middle"></slot>
        </div>
        <div>
            <slot name="right"></slot>
        </div>
    </div>
</template>
<script>
import Icon from '../common/Icon'
export default {
    name: 'checkbox',
    props: {
        value: {

        },
        id: {

        },
        checked: {
            type: Boolean,
            default: true
        },
        model:{

        },
        type: {

        },
        position: {

        }
    },
    components: {
        Icon
    },
    data() {
        return {
            changeModel: this.model
            //model: this.model,
            //  defaultType: this.type || 'checkbox'
        }
    },
    methods: {
        change(value) {
            this.$emit('change', value)
        }
    }
}
</script>
<style lang="less">
.z-checkbox {
    .zicon {
        margin: 0;
    }
}

.check-label {
    position: relative;
}

.boxcheck {
    display: none;
}

.z-check {
    opacity: 0;
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 11;
    &:checked+.boxcheck {
        display: flex;
        &+.boxnocheck {
            display: none;
        }
    }
}

.checkbox-miidle {
    padding-left: 0.2rem;
}
</style>