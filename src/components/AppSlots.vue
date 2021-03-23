<template>
    <div class="container pt-1">
        <div class="card">
            <h2>Slots</h2>
        </div>

        <app-list>
            <template #default="{idx, lists}">
          <span style="color: #c25205;">
              <srtong>{{idx}}</srtong>
              Item: {{lists}}
          </span>
            </template>
        </app-list>

        <app-block>
            <p>This is important text</p>
            <template #header>
                <h3>New Header!</h3>
            </template>

            <template #footer>
                <hr>
                <small>It is footer</small>
            </template>

        </app-block>
    </div>
</template>

<script>
    import AppBlock from "./components/AppBlock";
    import AppList from "./AppList";
    export default {

        components:{AppBlock, AppList}
    }
</script>

<style scoped>

</style>