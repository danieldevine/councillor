<template>
    <div class="councillor">
        <div class="fleg">
            <div></div>
            <div></div>
            <div></div>
        </div>
        <div v-if="surname">
            <h4>Your councillor name is:</h4>
            <h1>
                {{firstname}}
                <br>
                "{{nickname}}"
                <br>
                {{surname}}
            </h1>
        </div>
        <social-sharing
            url="https://danieldevine.github.io/councillor/"
            :title="`Vote #1 ${firstname} '${nickname}' ${surname}`"
            :description="`Vote #1 ${firstname} '${nickname}' ${surname}` "
            :quote="`Vote #1 ${firstname} '${nickname}' ${surname}` "
            hashtags="councillorName"
            twitter-user="coderjerk"
            inline-template
        >
            <div class="councillor__social">
                <div class="button">
                    <network network="facebook">
                        <i class="fab fa-facebook"></i> Facebook
                    </network>
                </div>
                <div class="button">
                    <network network="twitter">
                        <i class="fab fa-twitter"></i> Twitter
                    </network>
                </div>
            </div>
        </social-sharing>
    </div>
</template>
<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";
import { log } from "util";

export default {
    name: "home",
    components: {
        // HelloWorld
    },
    data() {
        return {
            surname: "",
            firstname: "",
            nickname: ""
        };
    },
    mounted() {
        this.getSurname();
        this.getFirstname();
        this.getNickname();
    },
    methods: {
        getSurname() {
            axios
                .get("/councillor/surnames.json")
                .then(result => {
                    let surnames = result.data.surnames;
                    this.surname =
                        surnames[Math.floor(Math.random() * surnames.length)];
                })
                .catch(err => {
                    console.log(err);
                });
        },
        getFirstname() {
            axios
                .get("/councillor/firstnames.json")
                .then(result => {
                    let firstnames = result.data.firstnames;
                    this.firstname =
                        firstnames[
                            Math.floor(Math.random() * firstnames.length)
                        ];
                })
                .catch(err => {
                    console.log(err);
                });
        },
        getNickname() {
            axios
                .get("/councillor/nicknames.json")
                .then(result => {
                    let nicknames = result.data.nicknames;
                    this.nickname =
                        nicknames[Math.floor(Math.random() * nicknames.length)];
                })
                .catch(err => {
                    console.log(err);
                });
        }
    }
};
</script>
<style lang="scss" scoped>
h1 {
    font-size: 8vw;
    line-height: 1;
}

h4 {
    font-size: 3vw;
    font-weight: 400;
}
</style>

