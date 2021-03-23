<template>
    <div class="container">
        <div class="card">
            <h2 v-color="myColor">Talk about directives</h2>

            <div class="form-control">
                <label for="inp">Default active</label>
                <input v-focus type="text" id="inp">
            </div>
            <button class="btn" @click="myColor = 'darkblue'">
                Make blue
            </button>
        </div>
    </div>
</template>

<script>
    import colorDirective from "./directives/colorDirective";
    import focusDirective from "./directives/focusDirective";

    export default {
        data() {
            return {
                myColor: 'coral'
            }
        },

        directives: {
            focus: focusDirective,
            color: colorDirective
        }
    }
</script>

<style scoped>

</style>