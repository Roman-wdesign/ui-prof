<template>
    <div class="container">
        <app-alert
                v-if="alert"
                text='This is very important message'
                title='Warning!'
                type='danger'
                closable
                @close="alert=false"
        ></app-alert>

        <div class="card">
            <button class="btn primary" @click="toggleAlert">{{alert ? 'Hide message' : 'Show message'}}</button>
        </div>
        <app-block></app-block>
    </div>
</template>

<script>
    import AppBlock from "./components/AppBlock";
    import AppAlert from "./components/AppAlert";
    import alertMixin from "./alertMixin";
    export default {
        mixins: [alertMixin],
        components: {AppAlert, AppBlock}
    }
</script>

<style scoped>

</style>