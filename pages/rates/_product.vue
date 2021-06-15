<template>
    <v-container>
        <div>{{ this.$route.params.product }}</div>
        <div>{{ this.$route.query.modal }}</div>
        <div>
            <ModalAddRate
                :show_modal="show_modal"
                :product="this.$route.params.product"
                :rates="getRatesSSR"
                @is-false="show_modal = false"
            />
        </div>
    </v-container>
</template>

<script>
import ModalAddRate from "../../components/ModalAddRate.vue";
export default {
    name: "selected_product",
    components: {
        ModalAddRate,
    },
    data() {
        return {
            show_modal: false,
            product_rates: ''
        };
    },
    async asyncData({ $axios }) {
        const getRatesSSR = await $axios.$get(
            `http://localhost:3456/api/rates/notebook`
        );
        return { getRatesSSR }
    },
    mounted() {
        if(this.$route.query.modal) {
            this.show_modal = true
        }
    }
};
</script>

<style lang="scss" scoped>
</style>