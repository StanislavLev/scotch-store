<template>
  <div class="product-details">
    <div class="container">
      <div class="row">
        <div class="col-xs-12" v-show="zoomImg">
          <img
            class="img-responsive" :src="product.image" alt="" @click="zoomImg=false" width=100%>
        </div>
        <div class="col-lg-4 col-md-4 col-sm-6 col-xs-12" v-show="!zoomImg">
          <img
            class="img-responsive" :src="product.image" alt="" @click="zoomImg=true">
        </div>
        <div class="col-lg-4 col-md-4 col-sm-3 col-xs-6">
          <p>
            <small>Details:</small><br/> {{product.description}}
          </p>
        </div>
        <div class="col-lg-4 col-md-4 col-sm-3 col-xs-6">
          <h3>{{product.name}}</h3>
          <p><small>Manufacturer: {{product.manufacturer && product.manufacturer.name}}</small></p>
          <p><small>Price:</small> ${{product.price}}</p>
          <product-button :product="product"></product-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import ProductButton from './ProductButton'
  export default {
    props: ['product'],
    components: {
      'product-button': ProductButton
    },
    data () {
      return {
        zoomImg: false
      }
    }
  }
</script>

<style>

  .product-details {
    border-bottom: 2px solid #F5F5F5;
    padding-top: 30px;
  }

  .product-details img:hover {
    cursor: pointer;
  }

  .product-details small {
    color: #808080;
  }
  
  .product-details h3 {
    margin: 0 0 10px;
  }

</style>
