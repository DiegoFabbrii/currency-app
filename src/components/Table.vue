<template>
    <main class="container">
        <table class="container__table">
            <thead class="table__header">
                <tr>
                    <th>Código</th>
                    <th>Nome</th>
                    <th>Compra</th>
                    <th>Venda</th>
                    <th>Máximo</th>
                    <th>Mínimo</th>
                    <th>Variação</th>
                </tr>
            </thead>

            <tbody class="table__body">
                <tr v-for="(coin, key) in coins" :key="key">
                    <td>{{ coin.code }}</td>
                    <td>{{ coin.name }}</td>
                    <td>{{ coin.bid }}</td>
                    <td>{{ coin.ask }}</td>
                    <td>{{ coin.high }}</td>
                    <td>{{ coin.low }}</td>
                    <td>
                        <span
                            class="table__body--pctChange"
                            :class="{
                                'table__body--pctChangeHigh':
                                    coin.pctChange > 0,

                                'table__body--pctChangeLow': coin.pctChange < 0,
                            }"
                            >{{ `${coin.pctChange} %` }}</span
                        >
                    </td>
                </tr>
            </tbody>
        </table>
    </main>
</template>

<script>
export default {
    name: "Table",
    props: {
        coins: Object,
    },
};
</script>

<style scoped>
.container {
    overflow-x: auto;
    width: 80vw;
}

.container__table {
    margin: 70px 0;
    width: 100%;
}

.table__body tr {
    border-bottom: 1px solid #333;
}

.table__header tr th,
.table__body tr td {
    padding: 20px;
    text-align: start;
    border-bottom: 1px solid #ccc;
}

.table__body {
    font-size: 1rem;
}

.table__body--pctChange {
    padding: 3px 7px;
    border-radius: 10px;
    background-color: #ddd;
}

.table__body--pctChangeHigh {
    background-color: rgb(37, 180, 80);
    color: #f7f7f7;
}

.table__body--pctChangeLow {
    background-color: rgb(190, 71, 63);
    color: #f7f7f7;
}
</style>
