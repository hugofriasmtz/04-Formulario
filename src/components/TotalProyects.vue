<template>
 
    <div class="row">
        <div class="col-6 my-3">
            <h3>
                Total de Proyectos: {{ NumProyects }}</h3>
        
        </div>
        <div class="col-6 text-end">
            <button @click="cleanData" class="btn btn-warning">Limpiar Proyecto</button>
        </div>
    </div>

    <div class="table-responsive">
        <table class="table table-dark table-hover">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Proyecto</th>
                    <th>Tipo</th>
                    <th>Urgente</th>
                    <th>Completado</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(proyect , index) in proyects" :key="index">
                    <td> {{index + 1}} </td>
                    <td> {{proyect.proyect}} </td>
                    <td> {{proyect.type}} </td>
                    <td @click="status(proyect, 'urgent')" :class="proyect.urgent ? 'bg-success': 'bg-danger'"> {{ proyect.urgent ? "Si" : "No" }} </td>
                    <td @click="status(proyect, 'filled')" :class="proyect.filled ? 'bg-success': 'bg-danger'"> {{ proyect.filled ? "Completado" : "Incompleto" }} </td>
                    
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        props: ['NumProyects', 'proyects', 'status', 'cleanData'],
       
    };
</script>