<template>

    <main class="o-main">

        <section class="o-section o-header">

            <img
                width="100%"
                height="100%"
                src="@/assets/a-wave.svg"
                alt="waves brackground"
                class="a-wave"
            >

            <div class="o-wrapper o-header__wrapper">

                <h1 class="a-title">
                    waves auth
                </h1>

                <h2 class="a-subtitle">
                    nuxtjs boilerplate
                </h2>

                <p class="a-text">
                    v 0.0.1
                </p>

            </div>

        </section>

        <section class="o-section o-auth">

            <div class="o-wrapper o-auth__wrapper">

                <button
                    @click="authenticateKeeper"
                    class="a-button"
                >
                    Authenticate
                </button>

                <div
                    v-show="address"
                    class="m-address"
                >
                    <p class="a-text">
                        {{ address }}
                    </p>
                </div>

            </div>

        </section>


    </main>

</template>

<script>

export default {

    data() {
        return {
            address: ''
        }
    },

    methods: {
        authenticateKeeper() {

             const authData = { data: "Autenticar meu Site" };

            if (WavesKeeper) {
                WavesKeeper.auth( authData )
                .then(auth => {
                    this.address = auth.address
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

<style scoped>

.o-section {
    width: 100%;
    height: 50vh;
    display: grid;
    justify-items: center;
    color: rgba(255, 255, 255, 0.67);
    text-align: center;
}

.a-wave {
    display: block;
    width: 100%;
    height: 100%;
    grid-column: 1 / 2;
    grid-row: 1 / 2;
}

.o-wrapper {
    width: 100%;
    padding: 2rem;
}

.o-header__wrapper {
    display: grid;
    grid-gap: 1rem;
    grid-column: 1 / 2;
    grid-row: 1 / 2;
    align-content: center;
}

.a-title {
    font-size: 2.25rem;
    font-weight: 500;
    color:rgba(255, 255, 255, 0.87);
}

.a-subtitle {
    font-size: 1.25rem;
    font-weight: 400;
    color: #FFDC00;
}

.a-text {
    color:rgba(255, 255, 255, 0.87);
    word-break: break-word;
}

.o-auth__wrapper {
    display: grid;
    align-content: center;
    justify-items: center;
    grid-gap: 1rem;
}

.a-button {
    padding: 1rem 0.875rem;
    font-size: 1.125rem;
    font-weight: 500;
    background-color: transparent;
    border: 1px solid rgba(255, 255, 255, 0.67);
    color:rgba(255, 255, 255, 0.87);
    border-radius: 0.3125rem;
    text-transform: uppercase;
    width: fit-content;
    transition: all 0.5s ease;
    cursor: pointer;
}
    .a-button:hover {
        border: 1px solid #FFDC00;
        color: #FFDC00;
    }

.m-address {
    padding: 2rem;
    border: 1px solid rgba(255, 255, 255, 0.67);
    display: grid;
    justify-items: center;
    align-items: center;
}

</style>
