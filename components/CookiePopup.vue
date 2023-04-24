<template>
    <div v-if="!cookieAccepted" class="cookie-popup">
        <div class="cookie-popup__content">
            <p>Deze website maakt gebruik van cookies om uw gebruikerservaring te verbeteren. Door gebruik te maken van onze
                website gaat u akkoord met ons <a href="#">cookiebeleid</a>.</p>
            <div>
                <button @click="acceptCookies">Ik ga akkoord</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            cookieAccepted: false
        };
    },
    methods: {
        acceptCookies() {
            this.cookieAccepted = true;
        },
    }
};
</script>

<style lang="scss">
$primary-color: #C850C0;
$box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);

.cookie-popup {
    position: fixed;
    bottom: 0;
    left: 5vw;
    right: 5vw;
    padding: 16px;
    background-color: #fff;
    box-shadow: $box-shadow;
    z-index: 1000;

    &__content {
        display: flex;
        justify-content: space-between;
        align-items: center;

        button {
            background-color: $primary-color;
            color: #fff;
            border: none;
            padding: 8px 16px;
            cursor: pointer;
            transition: background-color 0.3s;

            &:hover {
                background-color: #ffffff;
                color: #C850C0;
                border-color: #C850C0;
                border-width: 1px;
                border-style: solid;
            }
        }
    }
}
</style>
  