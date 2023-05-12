<template>
    <div class="help-guarantee">
        <MLoading v-if="showLoading"></MLoading>
        <div class="title-help-guarantee" style="font-weight: 600;">I. CHÍNH SÁCH BẢO HÀNH</div>
        <div class="content-help-guarantee">
            <p>1. Với mỗi chủng loại phụ tùng HAUI sẽ có một chính sách bảo hành khác nhau. Khách hàng sẽ được cung
                cấp thông tin chi tiết khi nhận hàng.</p>
            <p>2. Với những sản phẩm khách hàng có nhu cầu bảo hành 3 tuần HAUI sẽ có những
                mức giá phù hợp với thời gian bảo hành sản phẩm. Vì có rất nhiều khách</p>
            <p>3. hàng và nhiều loại sản phẩm không cần bảo hành thời gian để giảm chi phí giá thành sản phẩm.</p>
            <p>4. HAUI đảm bảo toàn bộ các sản phẩm bên HAUI cung cấp đạt đúng tiêu chuẩn , chất lượng như đã
                thống nhất khi báo giá cho khách hàng, để khách hàng có những sự lựa chọn phù hợp với nhu cầu.</p>
        </div>
        <div class="title-help-guarantee" style="font-weight: 600;">II. NHỮNG TRƯỜNG HỢP KHÔNG NẰM TRONG DANH MỤC BẢO HÀNH
        </div>
        <div class="content-help-guarantee">
            <p>1. Mất nhãn mác</p>
            <p>2. Dính vết bẩn</p>
            <p>3. Quá thời gian bảo hành</p>
            <p>4. Dính nhiều vết bẩn</p>
            
        </div>
        <p>Mọi thắc mắc Quý khách vui lòng liên hệ đến số điện thoại Hotline <b style="font-weight: 800;">0394061318</b> để
            biết thêm thông tin chi tiết.</p>
        <p>Cảm ơn Quý khách đã sử dụng sản phẩm và dịch vụ của <b style="font-weight: 800;">HAUI</b> !</p>
    </div>
</template>

<script>
import MLoading from '@/components/MLoading.vue';

export default {
    /**
     * Tên component
     */
    name: 'Guarantee',
    /**
     * Hứng nhận
     */
    props: [""],
    /**
     * Component được sử dụng
     */
    components: { MLoading },
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
            showLoading: false
        }
    },
    /**
     * Phương thức
     */
    methods: {

    },
    created() {
        this.showLoading = true;
        setTimeout(async () => {
            this.showLoading = false;
        }, 500);
    },
    /**
     * Theo dõi sự thay đổi
     */
    watch: {

    }
}
</script>

<style></style>