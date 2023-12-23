<template>
    <label for="input"
        :style="computeContainerStyles"
        @mouseenter="isHovered = true"
        @mouseleave="isHovered = false"
    >
        <slot name="left"></slot>
        <input
            id="input" :type="computeType"
            :style="computeInputStyles"
            :placeholder="placeholder"
        >
        <slot name="right"></slot>
    </label>
</template>

<script>
    export default {
        data() {
            return {
                isHovered: false
            };
        },

        props: {
            type: String,
            placeholder: String,
            containerDefaultStyles: Object,
            containerHoverStyles: Object,
            inputDefaultStyles: Object,
            inputHoverStyles: Object
        },

        computed: {
            computeType() {
                if (this.type == 'password' ||
                    this.type == 'email' ||
                    this.type == 'number')
                    return this.type;
                else
                    return 'text';
            },

            computeContainerStyles() {
                return {
                    ...this.containerDefaultStyles,
                    ...this.containerOnHover
                };
            },
            containerOnHover() {
                return this.isHovered ? this.containerHoverStyles : {};
            },
            computeInputStyles() {
                return {
                    ...this.inputDefaultStyles,
                    ...this.inputOnHover
                };
            },
            inputOnHover() {
                return this.isHovered ? this.inputHoverStyles : {};
            }
        }
    }
</script>

<style scoped>
    label {
        display: flex;
        align-items: center;
        gap: 10px;
        margin: 0;
        padding: 5px;
        overflow: hidden;

        border: 1px solid #876cbd;
        border-radius: 15px;
        background-color: rgba(242, 237, 247, 0.25);
        cursor: text;
    }

    input {
        width: 100%;
        margin: 0 5px;
        font-size: 15px;
        color: black;
        word-wrap: break-word;
        border: none;
        background-color: transparent;
        transition: 0.3s;
    }

    input:focus {
        outline: none;
    }
</style>