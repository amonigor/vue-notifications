<template>
    <div id="app">
        <button class="vn-button" @click.prevent="generateNotification">
            Generate Notification
        </button>

        <NotificationsBox
            position="bottom-right"
            :notifications="vnNotifications"
        />
    </div>
</template>

<script>
import NotificationsBox from "./components/NotificationsBox";

export default {
    name: "App",
    data() {
        return {
            vnNotifications: [],
        };
    },
    components: { NotificationsBox },
    methods: {
        generateNotification() {
            this.vnNotifications.push(
                {
                    title: "Vue notification " + Math.floor(Math.random() * 10),
                    icon: require("@/assets/logo.png"),
                    image: require("@/assets/logo.png"),
                    content:
                        "Fugiat eiusmod proident elit excepteur quis officia aute labore minim quis " +
                        Math.floor(Math.random() * 10),
                    // mainColor: "#42b883",
                    // backgroundColor: "#42b883",
                    // fontColor: "#ffffff",
                    // fontFamily: "'Patua One', cursive",
                    // border: {
                    //     size: "5px",
                    //     type: "solid",
                    //     color: "red",
                    //     radius: "15px",
                    // },
                }
            );

            this.removeNotification();
        },

        removeNotification() {
            setTimeout(() => {
                this.vnNotifications.shift();
            }, 3000);
        },
    },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Patua+One&display=swap");

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    background-color: #2c3e50;
    width: 100vw;
    height: 100vh;

    .vn-button {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);

        background-color: #42b883;
        border: none;
        outline: none;
        cursor: pointer;

        font-size: 15px;
        font-weight: bold;
        color: #ffffff;
        padding: 10px;
        border-radius: 5px;
    }
}
</style>
