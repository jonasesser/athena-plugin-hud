<template>
    <div class="stat-wrapper">
        <div class="split space-between">
            <div class="bar">
                <div class="bar-shadow"></div>
                <Icon :shadow="true" class="stat-icon" icon="icon-shield2" :size="18"></Icon>
                <div class="fill" :style="getFill">
                    <div class="fill-shine" :style="getFill" />
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, defineAsyncComponent } from 'vue';

const ComponentName = 'Armour';
export default defineComponent({
    name: ComponentName,
    components: {
        Icon: defineAsyncComponent(() => import('@components/Icon.vue')),
    },
    props: {
        value: {
            type: Number,
            default: 199,
        },
    },
    computed: {
        getFill() {
            return `height: ${this.value}% !important`;
        },
    },
});
</script>

<style scoped>
.stat-wrapper {
    display: flex;
    flex-direction: row;
}

.bar {
    display: block;
    position: relative;
    background: rgba(0, 0, 0, 0.5);
    box-sizing: border-box;
    min-width: 45px;
    max-width: 45px;
    min-height: 45px;
    max-height: 45px;
    border-radius: 45px;
    overflow: hidden;
    border: 2px solid rgba(0, 0, 0, 0.2);
    box-shadow: 0px 0px 0px 4px rgba(0, 0, 0, 0.2);
}

.bar-shadow {
    display: block;
    position: relative;
    box-sizing: border-box;
    min-width: 49px;
    max-width: 49px;
    min-height: 49px;
    max-height: 49px;
    border-radius: 50px;
    border: 2px solid rgba(0, 0, 0, 0.2);
    box-shadow: inset 0px 0px 0px 6px rgba(0, 0, 0, 0.3);
    z-index: 50;
    left: -4px;
    top: -4px;
    mix-blend-mode: overlay;
}

.stat-icon {
    display: flex;
    color: white;
    align-items: center;
    justify-content: center;
    min-width: 45px;
    max-width: 45px;
    min-height: 45px;
    max-height: 45px;
    position: absolute;
    z-index: 99;
    opacity: 0.5;
    left: -4px;
    top: -1px;
    mix-blend-mode: lighten;
}

.fill {
    position: absolute;
    background: #475e5e;
    z-index: 25;
    min-width: 65px;
    box-sizing: border-box;
    bottom: 0px;
    outline: 1px solid transparent;
    overflow: hidden;
}

.fill-shine {
    position: relative;
    background: #87b3b3;
    z-index: 30;
    min-width: 2px;
    max-width: 2px;
    min-height: 100px;
    box-sizing: border-box;
    top: -25px;
    animation: swipe 4s infinite linear;
    box-shadow: 0px 0px 10px 10px #87b3b3;
}

@keyframes swipe {
    0% {
        transform: translateX(-100px) rotate(45deg);
        opacity: 0;
    }
    25% {
        transform: translateX(40px) rotate(45deg);
        opacity: 0.8;
    }
    100% {
        transform: translateX(200px) rotate(45deg);
        opacity: 1;
    }
}
</style>
