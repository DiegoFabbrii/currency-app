<template>
    <h1>Cotação de moedas</h1>
    <Table :coins="coins" />
</template>

<script>
import { toRefs, reactive, onMounted } from "vue";
import axios from "axios";
import Table from "./components/Table.vue";

export default {
    name: "App",

    components: {
        Table,
    },

    setup() {
        const data = reactive({
            coins: {},
        });

        onMounted(async () => {
            const response = await axios.get(
                "https://economia.awesomeapi.com.br/json/all"
            );

            data.coins = response.data;
            console.log(data.coins);
        });

        return { ...toRefs(data) };
    },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap");

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: "Poppins", sans-serif;
}

h1 {
    margin-top: 70px;
    text-align: center;
}
</style>
