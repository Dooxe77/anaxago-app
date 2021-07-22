<template>
  <div class="product-infos">
    <div class="product-type">
      {{productInfos.type}}
    </div>
    <div class="product-name">
      {{productInfos.name}}
    </div>
    <div class="product-details-container">
      <!-- Component shared Key / value text -->
      <div class="product-key-value-infos">
        <span class="key">
          Instrument émis
        </span>
        <span class="value">
          {{productInfos.emittedInstrument}}
        </span>
      </div>
      <div class="product-key-value-infos">
        <span class="key">
          Horizon
        </span>
        <span class="value">
          {{productInfos.horizon}}
        </span>
      </div>
      <div class="product-key-value-infos">
        <span class="key">
          Distribution
        </span>
        <span class="value">
          {{productInfos.distribution}}
        </span>
      </div>
    </div>
    <img 
      :src="productInfos.imgUrl"
      alt="Product image" 
      width="800" 
      height="440">
      <span class="product-description">
        {{productInfos.description}}
      </span>
  </div>
</template>

<script>
export default {
  name: 'ProductInfos',
  props: {
    productInfos: {
      type: Object,
      required: true,
    }
  },
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

  .product-infos {
    height: 100%;

    .product-type {
      font-weight: 600;
      font-size: 14px;
      color: $nile-blue-color;
      line-height: 1.6;
    }

    .product-name {
      font-size: 28px;
      color: $nile-blue-color;
      line-height: 1.6;
      margin-bottom: 20px;
    }

    .product-details-container {
      display: flex;

      .product-key-value-infos {
        display: flex;
        flex-direction: column;
        flex: 1;
        margin-bottom: 20px;

        .key {
          font-size: 13px;
          line-height: 1.9;
          color: $cutty-sark-color;
          white-space: nowrap;
        }

        .value {
          display: flex;
          font-size: $font-size-text;
          line-height: 1.5;
          color: $nile-blue-color;
          white-space: nowrap;
          align-items: center;
          justify-content: space-between;
        }
      }
    }

    .product-description {
      font-size: $font-size-text;
      line-height: 2;
      color: $oxford-blue;
    }
  }
</style>
