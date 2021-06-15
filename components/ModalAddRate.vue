<template>
    <div>
        {{ rates }}
        <v-dialog v-model="add_rate" width="500">
            <template v-slot:activator="{ on, attrs }">
                <v-btn
                    color="success"
                    v-bind="attrs"
                    v-on="on"
                    @click="show_dialog = true"
                >
                    Avaliar
                </v-btn>
            </template>
            <v-card>
                <v-card-title
                    class="primary lighten-1 white--text"
                    :class="
                        $vuetify.breakpoint.xs ? 'text-subtitle-1' : 'text-h6'
                    "
                >
                    Avaliação
                </v-card-title>
                <v-card-subtitle
                    class="primary lighten-1 white--text font-weight-regular"
                    :class="
                        $vuetify.breakpoint.xs
                            ? 'text-caption'
                            : 'text-subtitle-2'
                    "
                >
                    Preencha o formulário para cadastrar sua avaliação!
                </v-card-subtitle>
                <v-card-text class="mt-3">
                    <v-text-field
                        :class="
                            $vuetify.breakpoint.xs
                                ? 'text-caption'
                                : 'text-subtitle-2'
                        "
                        label="Nome"
                        v-model="rate_object.firstName"
                    />
                    <v-text-field
                        :class="
                            $vuetify.breakpoint.xs
                                ? 'text-caption'
                                : 'text-subtitle-2'
                        "
                        label="Sobrenome"
                        v-model="rate_object.lastName"
                    />
                    <v-text-field
                        :class="
                            $vuetify.breakpoint.xs
                                ? 'text-caption'
                                : 'text-subtitle-2'
                        "
                        label="Idade"
                        v-model="rate_object.age"
                    />
                    <v-textarea
                        :class="
                            $vuetify.breakpoint.xs
                                ? 'text-caption'
                                : 'text-subtitle-2'
                        "
                        label="Avaliação"
                        v-model="rate_object.rate"
                    />
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions>
                    <v-btn color="error" text @click="isShowModalFalse">
                        Cancelar
                    </v-btn>
                    <v-spacer></v-spacer>
                    <v-btn color="primary" text @click="postRate">
                        Enviar
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
    name: "ModalAddrate_object",
    props: {
        show_modal: {
            type: Boolean,
        },
        product: {
            type: String,
        },
        rates: {
            type: Array
        }
    },
    data() {
        return {
            rate_object: {
                firstName: "",
                lastName: "",
                age: "",
                rate: "",
            },
            show_dialog: false,
            rates: [],
        };
    },
    methods: {
        async postRate() {
            this.isShowModalFalse();

            try {
                this.$axios.$post(
                    `http://localhost:3456/api/rates/${this.product}`,
                    this.rate_object
                );

                alert("Parabéns, sua avaliação foi postada!");

                this.rate_object.firstName = "";
                this.rate_object.lastName = "";
                this.rate_object.age = "";
                this.rate_object.rate = "";
            } catch (error) {
                alert("Houve algum erro, tente novamente!");
            }
        },
        isShowModalFalse() {
            this.show_dialog = false;
            this.$emit("is-false");
        },
    },
    computed: {
        add_rate() {
            return this.show_modal || this.show_dialog ? true : false;
        },
    },
};
</script>

<style>
</style>