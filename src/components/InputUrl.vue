<template>
  <div id="input-url">
    <input type="text" class="radius_left"/>
    <input class="radius_right" type="button" value="新增" />
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
$all_width: 900px;
$input_width: 600px;
$radius: 20px;
#input-url {
  display: flex;
  justify-content: center;
  height: 50px;
  margin: auto;
  width: $all_width;
  input{
    border: none;
  }
  input[type="text"]{
    width: $input_width;
  }
  input[type="button"]{
    width: $all_width - $input_width;
    background-color: lightgray;
    transition-duration: .2s;
    &:hover{
      background-color: darken(lightgray, 20%);
    }
  }
}
.radius_left{
  border-top-left-radius: $radius;
  border-bottom-left-radius: $radius;
}
.radius_right{
  border-top-right-radius: $radius;
  border-bottom-right-radius: $radius;
}
</style>
