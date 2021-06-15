<template>
    <v-container class="my-5">
        <v-row justify="center" align="center">
            <v-col
                cols="12"
                xs="12"
                md="6"
                lg="4"
                v-for="product in products"
                :key="product.id"
            >
                <v-card>
                    <v-card-title
                        :class="
                            $vuetify.breakpoint.xs
                                ? 'text-subtitle-1'
                                : 'text-h6'
                        "
                        class="font-weight-regular"
                        >{{ product.model }}</v-card-title
                    >
                    <v-card-text>
                        <v-img
                            contain
                            :width="$vuetify.breakpoint.xs ? '150' : '240'"
                            height="120"
                            class="mx-auto"
                            :src="product.img"
                        />
                        <v-expansion-panels class="mt-3">
                            <v-expansion-panel>
                                <v-expansion-panel-header>
                                    Especificações
                                </v-expansion-panel-header>
                                <v-expansion-panel-content>
                                    <ul>
                                        <li>
                                            <strong>Marca:</strong>
                                            {{ product.specs.brand }}
                                        </li>
                                        <li>
                                            <strong>Cor:</strong>
                                            {{ product.specs.color }}
                                        </li>
                                        <li v-html="product.specs.random" />
                                        <li>
                                            <strong>Lançamento:</strong>
                                            {{ product.specs.release }}
                                        </li>
                                        <li>
                                            <strong>Preço:</strong>
                                            {{ product.specs.price }}
                                        </li>
                                    </ul>
                                </v-expansion-panel-content>
                            </v-expansion-panel>
                        </v-expansion-panels>
                    </v-card-text>
                    <v-card-actions class="ml-2">
                        <v-btn color="success">
                            <nuxt-link :to="'/rates/' + product.query + '?modal=true'">
                                Avaliar
                            </nuxt-link>
                        </v-btn>
                        <v-btn color="info">
                            <nuxt-link :to="'/rates/' + product.query">
                                Ver avaliações
                            </nuxt-link>
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: "Products",
    data() {
        return {
            products: [
                {
                    id: 1,
                    model: "Universe S10",
                    query: "smartphone",
                    img: require("../static/universe_s10.jpg"),
                    specs: {
                        brand: "RandomPhone",
                        color: "Vermelho",
                        random: "<strong>Polegadas:</strong> 6.3",
                        release: "2017",
                        price: "986",
                    },
                },
                {
                    id: 2,
                    model: "Extreme U20",
                    query: "notebook",
                    img: require("../static/extreme_u20.jpg"),
                    specs: {
                        brand: "RandomNotebook",
                        color: "Cinza",
                        random: "<strong>Polegadas:</strong> 17",
                        release: "2019",
                        price: "3650",
                    },
                },
                {
                    id: 3,
                    model: "Carbon T1",
                    query: "smartv",
                    img: require("../static/carbon_t1.jpg"),
                    specs: {
                        brand: "RandomSmartv",
                        color: "Preto",
                        random: "<strong>Polegadas:</strong> 42",
                        release: "2021",
                        price: "4350",
                    },
                },
                {
                    id: 4,
                    model: "Smtw X4",
                    query: "smartwatch",
                    img: require("../static/smtw_x4.jpg"),
                    specs: {
                        brand: "RandomSmarwatch",
                        color: "Cinza",
                        random: "<strong>Polegadas:</strong> 3",
                        release: "2020",
                        price: "870",
                    },
                },
                {
                    id: 5,
                    model: "Ultramecha GT100",
                    query: "keyboard",
                    img: require("../static/ultramecha_gt100.jpg"),
                    specs: {
                        brand: "RandomKeyboard",
                        color: "Cinza Fosco",
                        random: "<strong>Padrão:</strong> ABNT2",
                        release: "2021",
                        price: "4350",
                    },
                },
                {
                    id: 6,
                    model: "Supersound HB1",
                    query: "headset",
                    img: require("../static/supersound_hb1.jpg"),
                    specs: {
                        brand: "RandomHeadset",
                        color: "Cinza Escuro",
                        random: "<strong>Bluetooth:</strong> Sim",
                        release: "2021",
                        price: "4350",
                    },
                },
            ],
        };
    },
};
</script>

<style lang="scss" scoped>
</style>