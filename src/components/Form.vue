<template>
    <div class="row">
        <div class="col-12 col-md-4">

            <progress-bar :porcentage="porcentage" />

            <form @submit.prevent="ProyectRegister" > 
                <div class="mb-3">
                  <label class="form-label">Proyecto</label>
                  <input v-model.trim="proyect" type="text" class="form-control" required/> 
                </div>
        
                <div class="mb-3">
                    <label class="form-label">Actividad</label>
                    <select v-model.trim="type" class="form-select" required>
                        <option disabled selected value="">Seleccione un tipo de actividad...</option>
                        <option>Aplicaciones Web con Vue.js</option>
                        <option>Backend Service con Node.js</option>
                        <option>App Movil con React Native</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-check-label">Urgente</label>
                    <input v-model.trim="urgent" type="checkbox" class="form-check-input" > 
                </div>
        
                <button type="submit" class="btn btn-primary">Guardar</button>
                
            </form>           
        </div>
        <div class="col-12 col-md-8">
            <total-proyects :NumProyects="NumProyects" :proyects="proyects" :status="status"/>
        </div> 
   </div>

</template>

<script>
    import ProgressBar from "./ProgressBar.vue";
    import TotalProyects from "./TotalProyects.vue";
    export default {
        data: () => ({
            proyect: "",
            type: "",
            urgent: false,
            proyects: [],
            
        }),
        methods: {
            ProyectRegister (){
                const proyect = {
                    proyect: this.proyect,
                    type: this.type,
                    urgent: this.urgent
                };


                this.proyects.push(proyect);
                this.saveData();
              
                this.proyect ="";
                this.type ="";
                this.urgent = false;
            },
            status (proyect, camp) {
                //this.urgent = !this.urgent;
                //this.proyects[id].urgent = !this.proyects[id].urgent;
                proyect[camp] = !proyect[camp];
                this.saveData();
            },
            saveData () {
                localStorage,setItem("proyects", JSON.stringify(this.proyects));
            },
            clearData () {
                this.proyects = [];
                localStorage.clear();
            },
        },
        computed: {
            NumProyects (){
               return this.proyects.length; 
            },
            porcentage (){
                let completeds = 0;
                this.proyects.map(proyect => {
                   if(proyect.completed) 
                    completeds++;
                });

                return (completeds * 100) / this.NumProyects  || 0;
            }
        },
        components: { ProgressBar, TotalProyects },
        
        mounted () {
            this.proyects = JSON.parse(localStorage.getItem("proyects")) || [];
        },
    };
</script>
