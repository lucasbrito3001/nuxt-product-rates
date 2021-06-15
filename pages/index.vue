<template>
    <v-app>
        <v-container fluid>
            <header class="my-5">
                <v-row>
                    <v-col cols="12">
                        <div
                            class="text-center font-weight-light"
                            :class="$vuetify.breakpoint.xs ? 'text-h6' : 'text-h4'"
                        >
                            Seja bem-vindo ao <span class="font-weight-bold">click rate!</span>
                        </div>
                        <div
                            class="text-center font-weight-light"
                            :class="$vuetify.breakpoint.xs ? 'text-subtitle-1' : 'text-h5'"
                        >
                            Aqui você pode avaliar os produtos que comprou postando seus comentários
                        </div>
                    </v-col>
                    <v-col cols="12">
                        <v-img width="64px" class="mx-auto" :src="require('../static/jackpot.png')"/>
                    </v-col>
                    <v-row align="center" class="mt-3 px-5">
                        <v-col cols="5"><hr></v-col>
                        <v-col cols="2" class="text-center">||</v-col>
                        <v-col cols="5"><hr></v-col>
                    </v-row>
                </v-row>
            </header>
            <v-row>
                <Products/>
            </v-row>
        </v-container>
    </v-app>
</template>

<script>
import Products from '../components/productsList.vue';
export default {
    name: 'Index',
    components: {
        Products
    }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;700&display=swap');
* {
    font-family: 'Quicksand', sans-serif;
}

.v-btn {
    text-transform: none;
}

a {
    text-decoration: none;
    color: white !important;
}
</style>