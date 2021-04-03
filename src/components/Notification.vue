<template>
    <div class="vn-notification" :style="vnVars" @click.prevent="vnRedirect">
        <div class="vn-header">
            <img v-if="icon" :src="icon" />
            <p>{{ title }}</p>
        </div>
        <div class="vn-body">
            <img src="@/assets/logo.png" />
            <p>
                Duis nulla amet elit proident et fugiat dolor id excepteur Lorem
                sint exercitation magna.
            </p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Notification",
    props: {
        // Values props
        title: {
            type: String,
            required: true,
            default: "Vue Notification",
        },
        icon: {
            type: String,
            required: false,
        },

        // Styling props
        mainColor: {
            type: String,
            required: false,
            default: "#ffffff",
        },
        backgroundColor: {
            type: String,
            required: false,
            default: "#cecece",
        },
    },
    computed: {
        vnVars() {
            return {
                "--main-color": this.mainColor,
                "--background-color": this.backgroundColor,
                "--border-radius": "10px",
            };
        },
    },
    methods: {
        vnRedirect() {

        }
    }
}
</script>

<style lang="scss">
.vn-notification {
    width: 350px;
    padding: 10px;
    border-radius: 5px;
    background-color: var(--background-color);
    cursor: pointer;
    opacity: 0.9;
    -webkit-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.4);
    -moz-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.4);
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.4);
    transition-duration: 0.2s;

    &:hover {
        opacity: 1;
    }

    .vn-header,
    .vn-body {
        display: flex;
        flex-direction: row;
        align-items: center;
        width: 100%;
    }

    .vn-header {
        justify-content: flex-start;

        img {
            width: 20px;
            height: 20px;
            margin-right: 10px;
        }

        p {
            font-weight: bold;
            font-size: 0.75em;
            opacity: 0.75;
        }
    }

    .vn-body {
        margin-top: 10px;
        justify-content: flex-start;

        img {
            width: 50px;
            height: 50px;
            border-radius: 100%;
            object-fit: cover;
            margin-right: 10px;
            background-color: #000000;
        }

        p {
            text-align: left;
            font-size: 0.9em;
        }
    }
}
</style>