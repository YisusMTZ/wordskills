<template>
    <div>
        {{Titulo}}
    </div>
</template>

<script>

export default {
    name: 'ColumnTable',
    props: {
        Hora : String,
        sesiones : Array
    },
    data(){
        return{
            Titulo : ''
        }
    },
    mounted(){
        this.ValidarSesiones();
    },
    methods :{
        ValidarSesiones(){
            this.sesiones.forEach(sesion => {
                let HoraSesion = sesion.start.substr(11,2);

                if(HoraSesion == this.Hora){
                    this.Titulo = sesion.title;
                }
            })
        }
    }
}
</script>