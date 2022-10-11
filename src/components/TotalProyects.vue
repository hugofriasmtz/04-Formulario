<template>
    <h3>
        Total de Proyectos: {{ NumProyects }}
    </h3>

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
        props: ['NumProyects', 'proyects', 'status'],

    };
</script>