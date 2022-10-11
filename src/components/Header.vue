<template>
    <div class="row">
        <div class="col-12 col-md-4">
          <h1>App - Proyectos</h1>
        </div>
        <div class="col-12 col-md-6">
          <img width="100" :src="url" :alt= "des">
        </div>
    </div>
    <hr />
</template>

<script>
    export default {
      data: () => ({
        url: "https://cdn.svgporn.com/logos/vue.svg",
        des: "Vue.js"
      }),
    };
</script>