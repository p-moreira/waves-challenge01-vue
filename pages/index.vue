<template>
    <div class="container">
        <div>
            <h1 class="title">
                Waves auth boilerplate
            </h1>
            <h2 class="subtitle">
                Waves blockchain auth using Waves Keeper and Nuxtjs
            </h2>
            <div class="links">
                <a
                    href="https://docs.wavesplatform.com/"
                    target="_blank"
                    class="button--grey"
                >
                    Waves Blockchain Documentation
                </a>
                <button
                    @click="authenticateKeeper"
                    class="button--grey"
                >
                    Authenticate
                </button>
            </div>
        </div>
    </div>
</template>

<script>

export default {

    methods: {
        authenticateKeeper() {

             const authData = { data: "Autenticar meu Site" };

            if (WavesKeeper) {
                WavesKeeper.auth( authData )
                .then(auth => {
                    console.log( auth ); //displaying the result on the console
                    /*...processing data */
                }).catch(error => {
                    console.error( error ); // displaying the result on the console
                    /*...processing errors */
                })
            } else {
                alert("Para autenticar o WavesKeeper precisa estar instalado.");
            }

        }
    },

}
</script>

<style>
.container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.title {
    font-family: "Quicksand", "Source Sans Pro", -apple-system,
        BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial,
        sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
}

.subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
}

.links {
    padding-top: 15px;
}
</style>
