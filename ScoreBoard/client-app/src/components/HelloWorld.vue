<template>
    <div class="hello">
        <!--<h1>{{ msg }}</h1>
        <p>
            For a guide and recipes on how to configure / customize this project,<br>
            check out the
            <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
        </p>
        <h3>Installed CLI Plugins</h3>
        <ul>
            <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
            <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
        </ul>
        <h3>Essential Links</h3>
        <ul>
            <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
            <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
            <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
            <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
            <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
        </ul>
        <h3>Ecosystem</h3>
        <ul>
            <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
            <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
            <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
            <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
            <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
            <li><button @click.prevent="addPoint()">Add Point</button></li>
        </ul>-->

        <table class="tableScoreBoard">
            <tr>
                <td>
                    <input ref="txtScoreA" class="inputScore" maxlength="2" value="0" disabled="disabled" />
                </td>
                <td>
                    <input ref="txtSetA" class="inputSet" maxlength="2" value="0" disabled="disabled" />
                    <input ref="txtSetB" class="inputSet" maxlength="2" value="0" disabled="disabled" />
                </td>
                <td>
                    <input ref="txtScoreB" class="inputScore" maxlength="2" value="0" disabled="disabled" />
                </td>
            </tr>
            <tr>
                <td>
                    <button class="buttonPoint" @click.prevent="decreasePointA()">-</button>
                    <button class="buttonPoint" @click.prevent="addPointA()">+</button>
                </td>
                <td>
                    <button @click.prevent="restartGame()">Reiniciar</button>
                </td>
                <td>
                    <button class="buttonPoint" @click.prevent="decreasePointB()">-</button>
                    <button class="buttonPoint" @click.prevent="addPointB()">+</button>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        methods: {
            async addPointA() {

                var txtScoreA = this.$refs.txtScoreA;
                var valueA = parseInt(txtScoreA.value);

                txtScoreA.value = (valueA + 1);
                valueA = parseInt(txtScoreA.value);

                var txtScoreB = this.$refs.txtScoreB;
                var valueB = parseInt(txtScoreB.value);

                if (valueA >= 25 && ((valueA - valueB) >= 2)) {
                    var txtSetA = this.$refs.txtSetA;
                    var valueSetA = parseInt(txtSetA.value);

                    txtSetA.value = (valueSetA + 1);

                    txtScoreA.value = 0;
                    txtScoreB.value = 0;
                }
            },
            async decreasePointA() {

                var txtScoreA = this.$refs.txtScoreA;
                var valueA = parseInt(txtScoreA.value);

                if (valueA > 0) {
                    txtScoreA.value = (valueA - 1);
                }
            },

            async addPointB() {

                var txtScoreB = this.$refs.txtScoreB;
                var valueB = parseInt(txtScoreB.value);

                txtScoreB.value = (valueB + 1);
                valueB = parseInt(txtScoreB.value);

                var txtScoreA = this.$refs.txtScoreA;
                var valueA = parseInt(txtScoreA.value);

                if (valueB >= 25 && ((valueB - valueA) >= 2)) {
                    var txtSetB = this.$refs.txtSetB;
                    var valueSetB = parseInt(txtSetB.value);

                    txtSetB.value = (valueSetB + 1);

                    txtScoreA.value = 0;
                    txtScoreB.value = 0;
                }
            },
            async decreasePointB() {

                var txtScoreB = this.$refs.txtScoreB;
                var valueB = parseInt(txtScoreB.value);

                if (valueB > 0) {
                    txtScoreB.value = (valueB - 1);
                }
            },
            async restartGame() {

                var txtScoreA = this.$refs.txtScoreA;
                txtScoreA.value = 0;

                var txtSetA = this.$refs.txtSetA;
                txtSetA.value = 0;
                var txtSetB = this.$refs.txtSetB;
                txtSetB.value = 0;

                var txtScoreB = this.$refs.txtScoreB;
                txtScoreB.value = 0;
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }

    input, button {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }

    .tableScoreBoard {
        position: absolute;
        margin: auto;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        width: 500px;
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }

    .inputScore {
        height: 150px; 
        width: 150px; 
        text-align: center; 
        font-size:100px;
    }

    .inputSet {
        height: 50px; 
        width: 50px; 
        text-align: center; 
        font-size:50px;
    }

    .buttonPoint {
        width:50px; 
        height:50px;
    }
</style>
