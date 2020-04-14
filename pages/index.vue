<template>
  <main class="listingPage">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xl-2 col-lg-3 md-4 col-sm-4">
          <!-- Sidebar -->
        </div>
        <!-- Main Content -->
        <div class="col-xl-10 col-lg-9 md-8 col-sm-8">
          <FeaturedProduct />

          <div class="mainResults">
            <ul class="s-result-list">
              <li v-for="product in products" :key="product._id" class="s-result-item celwidget">
                <div class="s-item-container">
                  <!-- Best seller -->
                  <div class="a-spacing-mico">
                    <div class="bestSeller">
                      <a href="#">Best Seller</a>
                    </div>
                  </div>
                  <div class="row">
                    <!-- Image -->
                    <div class="col-sm-3 text-center">
                      <a href="#">
                        <img :src="product.photo" style="with:150px;" class="img-fluid">
                      </a>
                    </div>
                    <div class="col-sm-9">
                      <div class="a-row a-spacing-small">
                        <!-- Date -->
                        <a href="#" class="a-link-normal">
                          <h2 class="a-size-medium">
                            {{ product.title }}
                            <sapn class="a-letter-space" />
                            <sapn class="a-letter-space" />
                            <sapn class="a-size-small a-color-secondary">Sep 3, 2019</sapn>
                          </h2>
                        </a>
                      </div>
                      <div class="a-row a-spacing-small">
                        <sapn class="a-size-small a-color-secondary">
                          by
                        </sapn>
                        <sapn class="a-size-small a-color-secondary">
                          <a class="a-link-normal a-text-normal">{{ product.owner.name }}</a>
                        </sapn>
                      </div>
                      <!-- Shipment -->
                      <div class="a-row">
                        <span class="a-size-small">Ship to USA</span>
                      </div>
                      <div class="row">
                        <div class="col-sm-7">
                          <div class="a-row a-pacing-none">
                            <a href="#" class="a-link-normal a-text-normal">Hardcover</a>
                          </div>
                          <!-- Price -->
                          <div class="a-row a-spacing-none">
                            <a href="#" class="a-link-normal a-text-normal">
                              <span class="a-offscreen">${{ product.price }}</span>
                              <span class="s-color-base sx-zero-spacing">
                                <span class="sx-price sx-price-large">
                                  <sup class="sx-price-currency">$</sup>
                                  <span class="sx-price-whole">{{ product.price }}</span>
                                  <sup class="sx-price-fractional">00</sup>
                                </span>
                              </span>
                            </a>
                            <sapn class="a-letter-space" />
                            <sapn class="a-size-base-plus a-color-secondary a-text-strike">
                              $28
                            </sapn>
                          </div>
                          <!-- Audible Trial -->
                          <div class="a-row a-spacing-none">
                            <span class="a-size-small a-color-secondary">
                              Free with Audible Trial
                            </span>
                          </div>
                          <hr>
                          <!-- Other Formats -->
                          <span class="a-size-small a-color-secondary">
                            Other Formats:
                            <span class="a-letter-space" />
                            <a href="#" class="a-size-small a-link-normal a-text-normal">Audio CD</a>
                          </span>
                        </div>
                        <!-- Ratings -->
                        <div class="col-sm-5">
                          <div class="a-row a-spacing-mini">
                            <!-- Star Ratings -->
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import FeaturedProduct from '~/components/FeaturedProduct'

export default {
  components: {
    FeaturedProduct
  },
  async asyncData ({ $axios }) {
    try {
      const response = await $axios.$get('/api/products')
      return {
        products: response.products
      }
    } catch (err) {
      console.log(err)
    }
  }
}
</script>
