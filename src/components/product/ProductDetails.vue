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
        <div class="col-lg-8 col-md-8 col-sm-6 col-xs-12 product-details__info">
          <div class="product-details__description">
            <small>{{product.manufacturer && product.manufacturer.name}}</small>
            <h3>{{product.name}}</h3>
            <div class="row" v-if="product.description.length > 200">
              <div class="col-sm-6 col-xs-12" v-if="product.description.length > 100">
                <p>
                  {{product.description.slice(0, (product.description.slice(product.description.length/2).indexOf(" "))+(product.description.length/2))}}
                </p>
              </div>  
              <div class="col-sm-6 col-xs-12">
                <p>
                  {{product.description.slice((product.description.slice(product.description.length/2).indexOf(" "))+(product.description.length/2))}}
                </p>
              </div>  
            </div>
            <p v-else>
              {{product.description}}
            </p>
          </div>
          <div class="product-details__price-cart">
            <p>${{product.price}}</p>
            <product-button :product="product"></product-button>
          </div>
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
    padding: 30px 0;
  }

  .product-details img:hover {
    cursor: pointer;
  }

  .product-details__description {
    padding-top: 30px;
  }

  .product-details__description small {
    color: #808080;
  }

  .product-details__description h3 {
    margin: 5px 0 30px 0;
  }

  .product-details__price-cart {
    display: flex;
    padding-top: 30px;
  }

  .product-details__price-cart p {
    flex-grow: 2;
    font-size: 20px;
    font-weight: bold;
  }
</style>
