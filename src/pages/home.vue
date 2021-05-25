<template >
    <div id="home">
        <titulo />
        <lista />
        <!-- <rodape /> -->
    </div>
</template>
<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"

import titulo from "../components/titulo"
import lista from "../components/lista"
// import rodape from "../components/rodape"
export default ({
    components: {
        titulo, lista
    }
})
</script>
<style scoped>
#home{
    height: 100vh;
}
</style>
