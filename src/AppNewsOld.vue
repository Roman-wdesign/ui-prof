<template>
    <div class="container pt-1">
        <div class="card">
            <h2>Actual news {{now}}</h2>
            <span>Has been opened yet: <strong>{{openRate}}</strong> | Was reading <strong>{{readRate}}</strong></span>
        </div>

        <AppNews
                v-for="item in news"
                :key="item.id"
                :title="item.title"
                :id="item.id"
                :is-open="item.isOpen"
                :was-read="item.wasRead"
                @open-news="openNews"
                @read-news="readNews"
                @unmark="unreadNews"
        />
    </div>
</template>

<script>
    import AppNews from "./components/AppNews";

    export default {
        data () {
            return {
                now: new Date().toLocaleDateString(),
                openRate: 0,
                readRate: 0,
                isOpen: false,
                news: [
                    {
                        title:  'I like Vue 3',
                        id: 1,
                        isOpen: false,
                        wasRead: false
                    },
                    {
                        title:   'I will be have a best job soon!',
                        id: 2,
                        isOpen: false,
                        wasRead: false
                    }
                ]
            }
        },
        provide() {
            return {
                title: 'List of News',
                news: this.news
            }
        },
        methods: {
            openNews (data) {
                this.openRate++ ;
                console.log(data);
            },
            readNews (id) {
                const idx = this.news.findIndex(news => news.id === id);
                this.news[idx].wasRead = true;
                this.readRate++ ;
            },
            unreadNews (id) {
                const news = this.news.find(news =>news.id === id);
                news.wasRead = false;
                this.readRate-- ;
            }
        },
        components: {
            AppNews
        }
    }
</script>

<style>
    h2 {
        color: coral;
    }
</style>
