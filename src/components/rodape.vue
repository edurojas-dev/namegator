<template>
  <div class="footer">
    <div class="container text-center">
      <p>Copyright ©</p>
      <p>Desenvolvido por <a href="#">Eduardo Rojas</a> <i class="fab fa-vuejs"></i></p>
    </div>
  </div>
</template>
<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
export default {
  name: "rodape",
};
</script>
<style scoped>
.footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  background-color: #D0D0D0;
  color: white;
  text-align: center;
}
</style>
