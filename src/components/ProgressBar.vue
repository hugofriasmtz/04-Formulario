<template lang="">
    <h3 class="text-center">Progreso: {{ porcentage }}%</h3>

    <div class="progress">
        <div class="progress-bar progress-bar-striped progress-bar-animated bg-success" role="progressbar" :aria-valuenow="porcentage" aria-valuemin="0" aria-valuemax="100" :style="`width:  ${porcentage}%`">
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            porcentage: Number,
        },
    };
</script>