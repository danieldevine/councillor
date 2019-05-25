<template>
    <div id="app">
        <router-view/>
    </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Heebo:500,900&display=swap");
@mixin base-typography {
    font-family: "Heebo", sans-serif;
    font-weight: 400;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-rendering: optimizeLegibility;
    line-height: 1.56;
}
* {
    box-sizing: border-box;
}
html {
    @include base-typography;
    padding: 0;
    margin: 0;
}
body {
    overflow-x: hidden;
    max-width: 100%;
    height: 100% !important;
    margin: 0 auto;
    position: relative;
}
h1,
h2,
h3,
h4,
h5,
h6 {
    margin: 0;
}
.councillor {
    width: 100vw;
    min-height: 100vh;
    padding: 4rem;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background: #cccccc;

    .fleg {
        position: fixed;
        width: 100%;
        display: grid;
        height: 60px;
        top: 0;
        grid-template-columns: repeat(3, 1fr);
        margin-top: 0;
        margin-bottom: auto;

        div {
            background: white;
            &:first-child {
                background: rgb(24, 158, 24);
            }

            &:last-child {
                background: rgb(240, 189, 48);
            }
        }
    }
}
.councillor__social {
    margin-top: 3rem;
}
.button {
    border: 1px solid black;
    padding: 1rem 2rem;
    display: inline-flex;
    cursor: pointer;

    &:first-child {
        margin-right: 1rem;
    }
}
</style>
