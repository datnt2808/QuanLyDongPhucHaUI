<template>
    <div>
        <TheHeader></TheHeader>
        <TheNavbar></TheNavbar>
        <div class="content">
            <TheLineLink name="Hệ thống gầm phanh"></TheLineLink>
            <div class="products-category">
                <div class="product-category-filter">
                    <div class="product-category-filter-header">Bộ lọc</div>
                    <div>
                        <label>Bộ lọc giá:</label>
                    </div>
                    <input type="range" v-model="priceRange" :min="minPrice" :max="maxPrice" style="width: 100%;" />
                    <br>
                    <span>Từ: {{ formatNumber(priceRange) }} - {{ formatNumber(maxPrice) }}</span>
                    <div>
                        <label for="">
                            Theo nhà sản xuất:
                        </label>
                        <div v-for="(item, index) in dataBrand" :key="index">
                            <input type="checkbox" :id="'checkbox-' + index" :value="item.brandID"
                                :checked="selectedItem == item.brandID" @change="trChange(item.brandID)">
                            <label :for="'checkbox-' + index" style="margin-left: 4px;">
                                {{ item.brandName }}
                            </label>
                        </div>
                    </div>
                </div>
                <div class="product-category-content">
                    <div class="product-category-title"
                        style="display: flex;align-items: center;height: 40px;justify-content: space-between;">
                        <div>
                            Danh sách sản phẩm
                        </div>
                        <div style="display: flex;align-items: center;">
                            Sắp xếp theo:
                            <MSelectBoxDown :data="[
                                    { feildShow: 'Ngày tạo gần nhất', feildValue: 'p.createdDate DESC' },
                                    { feildShow: 'Ngày sửa gần nhất', feildValue: 'p.modifiedDate DESC' },
                                    { feildShow: 'Theo giá tăng dần', feildValue: 'p.price ASC' },
                                    { feildShow: 'Theo giá giảm dần', feildValue: 'p.price DESC' },
                                    { feildShow: 'Tên sản phẩm a-z', feildValue: 'p.productName ASC' },
                                    { feildShow: 'Tên sản phẩm z-a', feildValue: 'p.productName DESC' },
                                ]" v-model="orderBy"></MSelectBoxDown>
                        </div>
                    </div>
                    <div class="list-product-category">
                        <div v-for="(item, index) in filteredProducts" :key="index"
                            :class="{ 'row-selected': rowSelected == item.productID }">
                            <div>
                                <div class="product">
                                    <div class="product-image">
                                        <img :src="item.image" alt="">
                                        <div class="favourtive" @click="favoriteProduct(item)">
                                            <i class="fa-solid fa-heart"></i>
                                        </div>
                                    </div>
                                    <div class="product-name" style="font-size: 15px;">{{ item.productName }}</div>
                                    <div class="price">{{ formatMoney(item.price) }}</div>
                                    <div class="product-buttom">
                                        <div class="product-detail" @click="detailProduct(item.productID)">Xem chi tiết
                                        </div>
                                        <div class="add-cart" @click="addCart(item)">Thêm vào giỏ hàng</div>
                                    </div>
                                </div>
                                <!-- </router-link> -->
                            </div>
                        </div>
                    </div>
                    <div class="see-more" @click="seeMoreImported">Xem thêm</div>
                </div>
            </div>
        </div>
        <TheFooter></TheFooter>
        <MLoading v-if="showLoading"></MLoading>
    </div>
</template>

<script>
import TheFooter from '@/layout/TheFooter.vue';
import TheHeader from '@/layout/TheHeader.vue';
import TheLineLink from '@/layout/TheLineLink.vue';
import TheNavbar from '@/layout/TheNavbar.vue';
import MCombobox from '@/components/MCombobox.vue'
import MLoading from '@/components/MLoading.vue';
import enumAUTO from '../../js/gEnum';
import axios from 'axios';
import { formatMoney, formatNumber } from '@/js/gCommon';
import MSelectBoxDown from '@/components/MSelectBoxDown.vue';
import ApiBrand from '../../js/apiBrand';

export default {
    /**
         * Tên component
         */
    name: 'ProdctByCategory',
    /**
     * Hứng nhận
     */
    props: [""],
    /**
     * Component được sử dụng
     */
    components: { TheHeader, TheNavbar, TheFooter, TheLineLink, MCombobox, MLoading, MSelectBoxDown },
    /**
     * Emit sự thay đổi
     */
    emits: [""],
    directives: {

    },
    /**
     * Data
     */
    data() {
        return {
            showLoading: false,
            listFilter: [],
            orderBy: 'p.modifiedDate DESC',
            pageIndex: 1,
            pageSize: 8,
            dataSearch: [],
            rowSelected: -1,
            priceRange: 0,
            dataBrand: [],
            selectedItem: null,
            keySearch: '',
        }
    },
    /**
     * Phương thức
     */
    methods: {
        formatNumber(number) {
            return formatNumber(number);
        },

        formatMoney(money) {
            return formatMoney(money);
        },

        getAllBrand() {
            axios.get(ApiBrand.getAll())
                .then((res) => {
                    if (res.status == 200) {
                        this.dataBrand = res.data;
                    } else {
                        this.dataBrand = null;
                    }
                })
        },
        getValue() {
            this.listFilter = [
                {
                    FieldName: "ProductCode",
                    Operator: enumAUTO.Operator.Like,
                    FilterValue: this.$store.state.search,
                },
                {
                    FieldName: "ProductName",
                    Operator: enumAUTO.Operator.Like,
                    FilterValue: this.$store.state.search,
                },
                {
                    FieldName: "PlaceOrigin",
                    Operator: enumAUTO.Operator.Like,
                    FilterValue: this.$store.state.search,
                },
                // {
                //     FieldName: "branchid",
                //     Operator: enumAUTO.Operator.Equal,
                //     FilterValue: this.$store.state.search,
                // },
            ];
            this.getDataRes();
        },

        getValueCategory() {
            this.listFilter = [
                {
                    FieldName: "ProductCode",
                    Operator: enumAUTO.Operator.Like,
                    FilterValue: this.$store.state.search,
                },
                {
                    FieldName: "ProductName",
                    Operator: enumAUTO.Operator.Like,
                    FilterValue: this.$store.state.search,
                },
                {
                    FieldName: "PlaceOrigin",
                    Operator: enumAUTO.Operator.Like,
                    FilterValue: this.$store.state.search,
                },
                // {
                //     FieldName: "branchid",
                //     Operator: enumAUTO.Operator.Equal,
                //     FilterValue: this.$store.state.search,
                // },
            ];
            this.getDataRes();
        },

        getDataRes() {
            this.showLoading = true;
            setTimeout(async () => {
                let objectFilter = {
                    pageIndex: this.pageIndex,
                    pageSize: this.pageSize,
                    listFilter: this.listFilter,
                    listOrderBy: this.orderBy
                }
                // console.log(objectFilter);
                await axios.post("https://localhost:7129/api/v1/Product/PagingProductByFilter", objectFilter)
                    .then((res) => {
                        if (res.status == 200) {
                            this.showLoading = false;
                            this.dataSearch = res.data.data;
                            // console.log(res);
                            // console.log(this.dataSearch);
                        }
                    })
            }, 500);
        },

        seeMoreImported() {
            this.pageSize = this.pageSize + 8;
            this.getDataRes();
        },

        detailProduct(item) {
            this.$router.push({ name: 'product', params: { id: item } });
        },

        addCart(data) {
            this.productCart = data;
            this.productCart.quantitys = this.number;
            // console.log(this.productCart);
            this.$store.commit('addToCart', this.productCart);
        },

        favoriteProduct(data) {
            if (!this.role) {
                alert("Bạn chưa đăng nhập");
            } else {
                this.productFavorite = data;
                this.$store.commit('addToCart', this.productFavorite);
            }
        },

        getAllBrand() {
            axios.get(ApiBrand.getAll())
                .then((res) => {
                    this.dataBrand = res.data;
                    // console.log(this.dataBrand);
                })
        },

        trChange(data) {
            if (this.selectedItem === data) {
                this.selectedItem = null;
            } else {
                this.selectedItem = data;
            }
            // console.log(this.selectedItem);
        }
    },
    created() {
        let param = this.$route.params.id;
        if (param) {
            this.getValueCategory();
            this.getAllBrand();
        } else {
            this.keySearch = this.$route.query.key;
            // console.log(this.keySearch);
            this.getValue();
            this.getAllBrand();
        }
    },
    /**
     * Theo dõi sự thay đổi
     */
    watch: {
        '$route.query.key': function (newVal) {
            console.log(newVal);
            this.getValue();
        },

        orderBy(newVal) {
            this.orderBy = newVal;
            this.getValue();
        },


    },

    computed: {
        filteredProducts() {
            // console.log(this.selectedItem);
            if (this.selectedItem == null) {

                return this.dataSearch.filter((product) => {
                    return product.price >= this.priceRange && product.price <= this.maxPrice;
                });
            }
            // console.log(this.selectedItem);
            return this.dataSearch.filter((product) => {
                return (product.price >= this.priceRange && product.price <= this.maxPrice) && product.brandID == this.selectedItem;
            });
        },

        minPrice() {
            return Math.min(...this.dataSearch.map((product) => product.price));
        },

        maxPrice() {
            return Math.max(...this.dataSearch.map((product) => product.price));
        },
    }
}
</script>

<style>
@import url(../../css/productcategory.css);
</style>