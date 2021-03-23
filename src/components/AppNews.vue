<template>
    <div class="card">
        <h3>{{title}}</h3>
        <app-button @action="open">
            {{isNewsOpen ? 'To close' : 'Open'}}
        </app-button>
        <app-button
                color="danger"
                v-if="wasRead"
                @action="$emit('unmark', id)">To check  unread</app-button>
        <div  v-if="isNewsOpen">
            <hr>
          <p>Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque
             laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur?</p>
            <app-button v-if="!wasRead" class="primary" @action="mark">To read this news</app-button>
            <app-news-list></app-news-list>
        </div>
    </div>
</template>
<script>
import AppButton from "./AppButton";
import AppNewsList from "./AppNewsList";
    export default {
        //props:['title']
        props: {

            wasRead: Boolean,
            title: {
                type: String,
                required: true
            },
            id: {
                type: Number,
                required: true
            },

            isOpen: {
                type: Boolean,
                required: false,
                default: false,
                validator(value){
                    return value === true || value === false
                }

            }
        },
        emits: {
            'open-news'(num) {
                if (num) {
                    return true
                }
                console.log('No data');
                return false
            },
            'read-news'(id) {
                if (id) {
                   return  true
                }
                console.warn('No id for emit read-news')
                return false
            },
            unmark: null
        },
        data(){
            return {
                isNewsOpen: this.isOpen
            }
        },
        methods: {
            open() {
                this.isNewsOpen = !this.isNewsOpen;
                if (this.isNewsOpen){
                    this.$emit('open-news', 55)
                }

            },
            mark(){
                this.isNewsOpen = false;
                this.$emit('read-news', this.id)
            },
            // unmark() {
            //     this.$emit('unmark', this.id)
            // }

        },
components:{AppButton, AppNewsList}
    }
</script>