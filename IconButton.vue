<template>
    <button
        :style="buttonStyles"
    >
        <span
            v-if="notifications != ''"
            :style="computeNotificationsStyles"    
        >
            {{ notifications }}
        </span>
        <slot></slot>
    </button>
</template>

<script>
    export default{
        props: {
            notifications: {
                type: String,
                default: ''
            },
            color: String,
            notificationsStyles: Object,
            buttonStyles: Object
        },

        computed: {
            computeNotificationsStyles() {
                return {
                    ...this.notificationsStyles,
                    '--main-color': this.color || '#fc2e53'
                };
            }
        }
    }
</script>

<style scoped>
    button {
        position: relative;
        padding: 10px;
        margin: 10px;
        cursor: pointer;
        border: none;
        background-color: transparent;
    }

    span {
        position: absolute;
        top: 0;
        right: 0;
        padding: 4px 10px;
        color: white;
        font: 10px Arial, sans-serif;
        box-shadow: 0 0 2.5px var(--main-color);
        border-radius: 10px;
        background-color: var(--main-color);
    }

    button img {
        height: 32px;
    }
</style>