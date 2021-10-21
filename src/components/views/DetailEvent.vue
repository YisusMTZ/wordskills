<template>
    <div>
        <div class="row">
            <div class="col-md-8">
                <h5>{{Event.name}}</h5>
            </div>
            <div class="col-md-4 d-grid">
                <button class="btn btn-primary">Register for this event
                </button>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-md-12">
                <TableEvent></TableEvent>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import TableEvent from '../TableEvent.vue'


export default{
    name : 'DetailEvent',
    components:{
        TableEvent
    },
    data(){
        return{
            OrganizerSlug: this.$route.params.SlugOrganizer,
            EventSlug: this.$route.params.SlugEvent,
            Event : {}
        }
    },
    mounted(){
        this.DatosEvento();
    },
    methods: {
        DatosEvento(){
            axios.get('organizer/' + this.OrganizerSlug + '/events/' + this.EventSlug)
            .then((Response) => {
                if(Response.status == 200) {
                    this.Event = Response.data;
                }
            })
            .catch((error) => {
                console.log(error);
            });
        }
    }
}
</script>
