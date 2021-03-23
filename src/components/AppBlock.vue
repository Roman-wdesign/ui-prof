<template>
    <div class="container">
        <app-alert
                v-if="alert"
                text='This is very important message'
                title='Warning!'
                @close="alert=false"
        ></app-alert>

        <div class="card">
            <button class="btn primary" @click="toggleAlert">{{alert ? 'Hide message' : 'Show message'}}</button>
        </div>
    </div>
</template>

<script>
    import AppAlert from "./AppAlert";
    import alertMixin from "../mixins/alertMixin";
    export default {
    mixins: [alertMixin],
   components: {AppAlert}
    }
</script>

<style scoped>

</style>