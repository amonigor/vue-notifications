<template>
    <div :class="`vn-box vn-${position}`">
        <transition-group name="vn-fade" mode="out-in">
            <Notification
                v-for="(notification, idx) in notifications"
                :key="(idx+1)"
                :icon="notification.icon"
                :title="notification.title"
                :image="notification.image"
                :content="notification.content"
                :main-color="notification.mainColor"
                :background-color="notification.backgroundColor"
                :font-family="notification.fontFamily"
                :font-color="notification.fontColor"
                :border="notification.border"
            />
        </transition-group>
    </div>
</template>

<script>
import Notification from "./Notification";

export default {
    name: "NotificationsBox",
    components: { Notification },
    props: {
        position: {
            type: String,
            required: false,
            default: "bottom-right",
        },
        notifications: {
            type: Array,
            required: true,
        },
    },
};
</script>

<style lang="scss">
.vn-box {
    display: flex;
    position: absolute;
    z-index: 999;

    &.vn-top-center,
    &.vn-bottom-center {
        left: 50%;
        transform: translateX(-50%);
    }

    &.vn-top-center,
    &.vn-top-left,
    &.vn-top-right {
        flex-direction: column-reverse;
        margin-top: 15px;

        .vn-notification {
            margin-bottom: 10px;
        }
    }

    &.vn-bottom-center,
    &.vn-bottom-left,
    &.vn-bottom-right {
        flex-direction: column;
        bottom: 0;
        margin-top: 0 !important;
        margin-bottom: 15px !important;

        .vn-notification {
            margin-top: 10px;
        }
    }

    &.vn-top-left,
    &.vn-bottom-left {
        left: 0;
        margin: 15px 0 0 15px;
    }

    &.vn-top-right,
    &.vn-bottom-right {
        right: 0;
        margin: 15px 15px 0 0;
    }
}

.vn-fade-enter-active,
.vn-fade-leave-active {
    transition: opacity 0.3s;
}

.vn-fade-enter,
.vn-fade-leave-to {
    opacity: 0;
}

@media only screen and (max-width: 500px) {
    .vn-box {
        justify-content: center;

        &.vn-top-center,
        &.vn-top-left,
        &.vn-top-right,
        &.vn-bottom-center,
        &.vn-bottom-left,
        &.vn-bottom-right {
            margin-left: 15px;
            margin-right: 15px;

            .vn-notification {
                width: 100%;
            }
        }

        &.vn-top-center,
        &.vn-bottom-center {
            left: 0;
            transform: translateX(0);
        }
    }
}
</style>