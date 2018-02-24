<template>
    <div class="modal__backdrop" @click="close" v-show="open">
        <transition name="modal" mode="out-in">
            <div class="modal" v-show="open" @click.stop>
                <header class="modal__header">
                    <h2 class="modal__title">{{ title }}</h2>
                    <button class="modal__close" @click="close">X</button>
                </header>
                <div class="modal__body">
                    <slot name="body"></slot>
                </div>
                <footer class="modal__footer">
                    <slot name="footer"></slot>
                </footer>
            </div>
        </transition>
    </div>
</template>

<script>
    export default {
        name: 'modal',
        props: {
            title: {
                type: String,
                required: false
            },
            open: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            close() {
                this.$emit('close');
                document.body.style.overflow = '';
            }
        },
        updated() {
            if (this.open) document.body.style.overflow = 'hidden';
        }
    }
</script>

<style lang="scss">
    $modal-z-index: 10;
    $white: #fff;
    $gray: #777;
    .modal__backdrop {
        z-index: $modal-z-index;
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.5);
        overflow-y: auto;
    }
    
    .modal {
        z-index: $modal-z-index + 1;
        box-sizing: border-box;
        position: absolute;
        top: 20%;
        left: 50%;
        opacity: 1;
        transform: translateX(-50%) scale(1);
        width: 90%;
        max-width: 600px;
        background-color: $white;
        border-radius: 4px;
        padding: 20px;
        margin-bottom: 40px;
    }
    
    .modal__title {
        font-size: 16px;
        color: $gray;
        padding: 0 20px 0 0;
        margin: 0;
        position: relative;
    }
    
    .modal__close {
        font-size: 16px;
        color: $gray;
        float: right;
        width: auto;
        padding: 20px;
        border: 0;
        cursor: pointer;
        background-color: transparent;
        position: absolute;
        top: 0;
        right: 0;
        &:hover {
            background-color: #eee;
        }
    }
    
    .modal__body {
        padding: 20px 0;
    }
    
    .modal__footer {
        text-align: right;
    }
    
    .modal-enter-active,
    .modal-leave-active {
        transition: all 100ms ease;
    }
    
    .modal-enter,
    .modal-leave-to {
        opacity: 0;
        transform: translateX(-50%) scale(.8);
    }
</style>
