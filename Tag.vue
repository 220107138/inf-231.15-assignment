<template>
    <span
        :style="computeStyles"
        @mouseenter="isHovered = true"
        @mouseleave="isHovered = false"
    >
        <slot></slot>
    </span>
</template>

<script>
    export default {
        data() {
            return {
                isHovered: false
            };
        },

        props: {
            defaultStyles: Object,
            hoverStyles: Object
        },

        computed: {
            computeStyles() {
                return {
                    ...this.defaultStyles,
                    ...this.stylesOnHover
                };
            },
            styleOnHover() {
                return this.isHovered ? this.hoverStyles : {};
            }
        }
    }
</script>

<style scoped>
    span {
        padding: 5px 10px;
        margin: 5px;
        font: 10px Arial, sans-serif;
        color: #876cbd;
        cursor: default;
        border-radius: 10px;
        background-color: rgba(196,180,220, 0.5);
    }
</style>