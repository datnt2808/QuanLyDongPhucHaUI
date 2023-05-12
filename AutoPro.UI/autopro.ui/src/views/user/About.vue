<template>
    <div>
        <TheHeader></TheHeader>
        <TheNavbar></TheNavbar>
        <div class="about" id="main">
            <MLoading v-if="showLoading"></MLoading>
            <TheLineLink name="Giới thiệu"></TheLineLink>
            <div class="about1">
                <div class="title-about">GIỚI THIỆU VỀ HAUI</div>
                <div class="content-about">Hệ thống quản lý đồng phục trường đại học công nghiệp Hà Nội - Trang phân phối độc
                    quyền về đồng phục của Trường đại học Công nghiệp Hà Nội
                </div>
                <img src="../../assets/Image/a1.jpg" alt="" style="width: 100px; height:100px ; margin-left: 40%;">
            </div>
            <div class="about1">
                <div class="title-about">Khảo sát hiện nay </div>
                <div class="content-about">Do nhu cầu đòi hỏi ngày càng cao của xã hội cũng như của con 
                người ngày càng cao, do đó để đáp ứng được yêu cầu của khách hàng thì phải luôn đổi mới và
                 hoàn thiện hơn. Hiện nay do xã hội phát triển không ngừng và kéo theo là sự lớn mạnh của 
                 các doanh nghiệp, của các tổ chức, chính vì vậy mà việc quản lí sao cho chặt chẽ là nhu cầu cấp 
                 thiết các doanh nghiệp. Lĩnh vực quản lí hàng hóa trong các doanh nghiệp hiện nay đang có nhu cầu rất lớn
                  vì số lượng hàng hoá được nhập và xuất trong một thời điểm là rất lớn và đòi hỏi chính xác, đồng thời thời gian cũng 
                  là yếu tố quan trọng. Thực tế hiện nay có rất nhiều doanh nghiệp lớn quản lí hàng hoá bằng phương pháp thủ công và bán
                 thủ công. Nếu có một công cụ quản lí hàng hóa đáp ứng được các yêu cầu của nghiệp vụ cũng như đòi hỏi của của công việc thì
                 đây sẽ là một thị trường lớn đầy tiềm năng phát triển.<br>
                Việc ứng dụng CNTT đã mang lại bước đột phá mới cho công tác quản lý kho, giúp doanh nghiệp nắm bắt được thông tin về hàng hóa,
                 vật tư, nguyên vật liệu và sản phẩm một cách chính xác kịp thời. Từ đó, người quản lý doanh nghiệp có thể đưa ra các kế hoạch và 
                 quyết định đúng đắn, giảm chi phí và tăng khả năng cạnh tranh, nâng cao kết quả hoạt động sản xuất kinh doanh. Để xử lý thông tin 
                 nhanh chóng, đầy đủ và chính xác và có hiệu quả thì ngành công nghệ thông tin đã phát triển tương đối phổ biến trên thế giới 
                 nói chung và Việt Nam nói riêng và đã cung cấp cho chúng ta những biện pháp cần thiết đó. Đã qua thời tính toán, sắp xếp và lưu trữ
                  thông tin thủ công truyền thống mang nặng tính chất lạc hậu, lỗi thời. Công nghệ thông tin đã đi vào các ngành với một phương thức
                 hoạt động hoàn toàn mới mẻ, sáng tạo và nhanh chóng mà không mất đi sự chính xác. Đặc biệt, nó đã đánh dấu một bước ngoặt trong 
                 việc áp dụng tin học vào trong hệ thống quản lý. Để đáp ứng nhu cầu ngày càng cao của khách hàng, doanh nghiệp phải đáp ứng đúng
                 những mong muốn của khách hàng về mặt hàng và thời gian họ cần. Doanh nghiệp cần đạt được những yếu tố mới mang lại sự hoàn thiện 
                 trong khả năng bán hàng, đó là khả năng cung cấp dịch vụ nhanh.
                </div>
            </div>
            <div class="about1">
                <div class="title-about">Quá trình hình thành</div>
                <div class="content-about">Hằng năm, số lượng sinh viên Trường Đại học Công nghiệp Hà Nội đăng ký đặt mua quần áo
                     đồng phục lên đến con số hàng nghìn.Tuy nhiên hiện tại, công việc quản lý đồng phục vẫn phải thực hiện thủ công: 
                     Giáo viên thể chất và giáo viên quân sự sẽ yêu cầu sinh viên điền thông tin vào danh sách đăng kí đặt mua, thuê đồng phục
                      và gửi lên trung tâm giáo dục thể chất. Điều đó gây khó khăn và tốn rất nhiều thời gian công sức trong quá trình quản lý. 
                      Đặc biệt với bối cảnh hiện nay, với số lượng sinh viên ngày càng gia tăng, thì việc quản lý càng trở nên khó khăn . Xuất phát
                     từ vấn đề đó, bản thân là sinh viên của Trường Đại học Công nghiệp Hà Nội, muốn góp phần nhỏ để giúp đỡ các thầy cô trong việc
                      quản lý đồng phục nên em đã xây dựng phần mềm “Quản lí Đồng phục”.
                </div>
            </div>
            <div class="about1">
                <div class="title-about">Mục tiêu
                </div>
                <div class="content-about">Trở thành trang quản lý hàng đầu tại Việt Nam. Không chỉ giúp cho sinh viên không chỉ Trường đại học Công nghiệp HÀ Nội
                    mà hướng đến sinh viên khắp khu vực miền Bắc có thể dễ dàng đặt mua đồng phục một cách nhanh gọn và dễ dàng nhất.
                </div>
            </div>
           <!--  <div class="about1">
                <div class="title-about">Giá trị cốt lõi
                </div>
                <div class="content-about">TÂM: AUTOPRO luôn lấy chữ TÂM để phục vụ Khách hàng, Đối tác
                </div>
                <div class="content-about">TÍN: AUTOPRO luôn lấy chữ TÍN để xây dựng thương hiệu và bảo vệ chữ TÍN như bảo
                    vệ tính mạng của chính mình</div>
                <div class="content-about">NHÂN: AUTOPRO luôn lấy chữ NHÂN để tạo dựng doanh nghiệp phát triển bền vững và
                    trường tồn</div>
            </div>
            <div class="about1">
                <div class="title-about"></div>
                <div class="content-about">
                    Với phương châm cùng hợp tác - cùng phát triển bền vững, chúng tôi cam kết luôn mang đến cho Quý Đối
                    tác: CHẤT LƯỢNG TỐT NHẤT - GIÁ CẢ HỢP LÝ NHẤT - DỊCH VỤ TỐT NHẤT. Chúng tôi rất tin tưởng vào sự thành
                    công tốt đẹp và lâu dài trong quá trình hợp tác giữa chúng tôi và Quý Khách hàng - Quý Đối tác.
                </div>
            </div> -->
        </div>
        <TheFooter></TheFooter>
    </div>
</template>
  
<script>
import TheFooter from '@/layout/TheFooter.vue';
import TheHeader from '@/layout/TheHeader.vue';
import TheLineLink from '@/layout/TheLineLink.vue';
import TheNavbar from '@/layout/TheNavbar.vue';
import MLoading from '@/components/MLoading.vue';

export default {
    /**
     * Tên component
     */
    name: 'About',
    /**
     * Hứng nhận
     */
    props: [""],
    /**
     * Component được sử dụng
     */
    components: { TheHeader, TheNavbar, TheFooter, TheLineLink, MLoading },
    /**
     * Emit sự thay đổi
     */
    emits: ["update:showLoading"],
    directives: {

    },
    /**
     * Data
     */
    data() {
        return {
            showLoading: false,
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

    },
    mounted() {

    }
}
</script>
  
<style>
@import url(../../css/about.css);
</style>