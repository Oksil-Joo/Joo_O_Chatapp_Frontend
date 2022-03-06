<template>
    <div class="message-panel">
        <div class="message-wrapper">
            <h1>{{ user }} says: </h1>
            <p class="message-text">
                {{ message }}
            </p>
        </div>
    </div>
</template>

<script>
export default {
    name: "TheChatMessage",

    props: {
        user: String,
        message: String
    }
}
</script>

<style lang="scss">
  .message-panel {
        float: left;
        clear: both;
        width: 51%;
        background-color: rgb(243, 255, 10);
        margin-bottom:1em;
        padding: 1em;
        border-radius: 10px;
        display: flex;

  .user-initial {
        position: relative;
         height: 48px;
         flex: 0 0 48px;
         background-color: rgab(255, 255, 255, 0.5);
         border-radius: 50%;
        text-transform: uppercase;
        font-size: 2em;

        span {
            position: absolute;
            top: 50%;
            left: 50%;
            -moz-transform: translate(-50%, -50%);
            transform: translate(-50%, -50%);
            }

        }
        .message-wrapper {
            margin-left: 1em;
        }
}

</style>