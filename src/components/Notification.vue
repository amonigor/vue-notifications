<template>
    <div class="vn-notification" :style="vnVars" @click.prevent="vnRedirect">
        <div class="vn-header">
            <img v-if="icon" :src="icon" />
            <p>{{ title }}</p>
        </div>
        <div class="vn-body">
            <img v-if="image" :src="image" />
            <p>{{ content }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Notification",
    props: {
        title: {
            type: String,
            required: true,
            default: "Vue Notification",
        },
        icon: {
            type: String,
            required: false,
        },
        image: {
            type: String,
            required: false,
        },
        content: {
            type: String,
            required: true,
        },
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
        fontFamily: {
            type: String,
            required: false,
            default: "Avenir, Helvetica, Arial, sans-serif",
        },
        fontColor: {
            type: String,
            required: false,
            default: "#000000",
        },
        border: {
            type: Object,
            required: false,
            default: function () {
                return {
                    size: "0px",
                    type: "solid",
                    color: "#cecece",
                    radius: "5px"
                };
            },
        },
    },
    computed: {
        vnVars() {
            return {
                "--main-color": this.mainColor,
                "--background-color": this.backgroundColor,
                "--font-family": this.fontFamily,
                "--font-color": this.fontColor,
                "--border": `${this.border.size} ${this.border.type} ${this.border.color}`,
                "--border-radius": `${this.border.radius}`,
            };
        },
    },
    methods: {
        vnRedirect() {},
    },
};
</script>

<style lang="scss">
.vn-notification {
    width: 350px;
    padding: 10px;
    border: var(--border);
    border-radius: var(--border-radius);
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
            margin-right: 5px;
        }

        p {
            font-family: var(--font-family);
            color: var(--font-color);
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
            background-color: var(--main-color);
        }

        p {
            font-family: var(--font-family);
            color: var(--font-color);
            text-align: left;
            font-size: 0.9em;
        }
    }
}
</style>