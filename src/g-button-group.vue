<template>
    <div class="g-button-group">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "g-button-group",
        mounted() {
            for(let node of this.$el.children) {
                if(node.nodeName.toLowerCase() !== 'button') {
                    console.warn('g-button-group 的子元素应该全是 g-button')
                }
            }
        }
    }
</script>

<style scoped lang="scss">
    .g-button-group {
        display: inline-flex;
        vertical-align: center;
        > .g-button {
            border-radius: 0;
            &:not(:first-child) {
                margin-left: -1px;
            }
            &:first-child {
                border-top-left-radius: var(--border-radius);
                border-bottom-left-radius: var(--border-radius);
            }
            &:last-child {
                border-top-right-radius: var(--border-radius);
                border-bottom-right-radius: var(--border-radius);
            }
            &:hover {
                position: relative;
                z-index: 1;
            }
        }
    }
</style>