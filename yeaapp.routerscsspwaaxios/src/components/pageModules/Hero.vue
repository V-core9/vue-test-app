<template>
    <div class="hero" >
        <div class="heroInner">
            <div class="contentSide">
                <h1>{{ title }}</h1>
                <p>{{ subtitle }}</p>
                <router-link v-bind:to="url" class="btn">{{ button }}</router-link>
            </div>
            <div class="imgSide">
                <img src="../../assets/logo.png">
            </div>
        </div>
  </div>
</template>

<script>


export default {
    name: 'Hero',
    props: {
        title: String,
        subtitle: String,
        button: String,
        url: String,
        img: String,
        backImg: String,
    },
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

    .hero {        
        display: flex;
        flex-direction: row;
        background: url("../../assets/back.jpg");
        min-height: 70vh;
        background-position: center;
        background-attachment: fixed;

        .heroInner{
            display: flex;
            flex-direction: row;
            align-items: center;
            max-width: 1300px;
            margin: 0 auto;
            justify-content: space-evenly;

            .btn {
                background: #8a0000;
                text-decoration: none;
                padding: 0.5em 1em;
                color: white;
                border-radius: 0.25em;
                font-size: 1.25em;
                width: max-content;
                margin-top: 1em;
            }

            .contentSide {
                align-content: flex-start;
                display: flex;
                flex-direction: column;
                text-align: left;
                gap: 1em;

                h1 {
                    font-size: 3.5em;
                    color: #ce0000;
                }

                p {
                    color: orange;
                    font-size: 1.5em;
                }
            }
        }
    }

</style>
