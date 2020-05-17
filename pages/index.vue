<template>
  <div class="container">
    <div class="header">
      <div class="header__item header_logo">
        <div class="header_logo__icon">
          <img alt="logo" src="/img/logoColor.svg">
        </div>
        <div class="header_logo__text">
          <img alt="logo" src="/img/textLogo.svg">
        </div>
      </div>
      <div class="header__item header_nav">
        <ul class="header_nav__list">
          <li class="header_nav__list_item"
              v-for="value in cate"
              :class="value.shared_url === is_selected ? 'header_nav__item_selected' : ''"
              @click="changeCate(value.shared_url)"
          >
            {{value.name}}
          </li>
        </ul>
      </div>
      <div class="header__item header_login">
        <img alt="logo" src="/img/login.svg">
      </div>
    </div>
    <div class="content">
      <div class="highLight-post">
        <div class="highLight-post__image">
          <img
            alt="dell"
            :src="res[0].thumbnail">
        </div>
        <div class="highLight-post__info">
          <span class="highLight-post__type--space">{{res[0].category.name}}</span>
          <span>By <span class="highLight-post__author">{{ res[0].created_by.name }}</span></span>
          <span> | {{ res[0].created_at }}</span>
        </div>
        <div class="highLight-post__title">
          <p>{{ res[0].title }}</p>
        </div>
        <div class="highLight-post__detail">
          <p>{{ res[0].description }}</p>
        </div>
      </div>
      <div class="list-post">
        <div v-for="(value , index) in res" class="post-item-cover" :key="index" v-if="index > 0">
          <div class="post-items">
            <div class="highLight-post__image">
              <img alt="dell"
                   :src="value.thumbnail">
            </div>
            <div class="highLight-post__info">
              <span class="highLight-post__type--space">{{value.category.name}}</span>
              <span>By <span class="highLight-post__author"> {{ value.created_by.name }} </span></span>
              <span> | {{ value.created_at }}</span>
            </div>
            <div class="highLight-post__title">
              <p>{{ value.title }}</p>
            </div>
            <div class="highLight-post__detail">
              <p>{{ value.description }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="loadMore">
        <div v-if="page === 1" class="loadMore__btn" @click="loadMore"><span>Xem thêm</span></div>
      </div>
    </div>
    <div class="footer">
      <div class="footer-content">
        <div class="footer-content-left">
          <div class="footer-left__logo">
            <div class="footer-left__logo-icon">
              <img alt="logo" src="/img/logo.svg">
            </div>
            <div class="footer-left__logo-text">
              <img alt="logo" src="/img/textLogoFooter.svg">
            </div>
          </div>
          <div class="footer-left__content">
            <div class="footer-left__content-product">
              <p>Sản phẩm và dịch vụ</p>
              <div class="footer-product__list">
                <ul>
                  <li>laptop DELL</li>
                  <li>Laptop HP</li>
                  <li>Laptop ThinkPad</li>
                  <li>AliendWare</li>
                  <li>Laptop Lenovo</li>
                  <li>Laptop Razer</li>
                </ul>
                <ul>
                  <li>laptop Asus</li>
                  <li>Macbook</li>
                  <li>Phụ Kiện</li>
                  <li>Bảo trì máy tính</li>
                </ul>
              </div>
            </div>
            <div class="footer-left__content-policy">
              <p>Chính sách</p>
              <ul>
                <li>Bảo hành</li>
                <li>Vận Chuyển</li>
                <li>Thanh Toán</li>
              </ul>
            </div>
            <div class="footer-left__content-about-us">
              <p>Về Think Pro</p>
              <ul>
                <li>Lịch sử thành lập</li>
                <li>Giá trị cốt lõi</li>
                <li>Tầm nhìn</li>
                <li>Sứ mệnh</li>
                <li>Hỏi đáp</li>
              </ul>
            </div>
          </div>
        </div>
        <div class="footer-content-right">
          <div class="footer-content-right__contact">
            <p style="opacity: 0.5">Hotline</p>
            <div class="footer-content-right__social">
              <div class="phone">1900.63.3579</div>
              <div class="social">
                <span><img alt="youtube" src="/img/youtube.svg"></span>
                <span><img alt="facebook" src="/img/facebook.svg"></span>
                <span><img alt="insta" src="/img/insta.svg"></span>
              </div>
            </div>
          </div>
          <p class="shop-system">Hệ Thống cửa hàng</p>
          <div class="footer-content-right__store">
            <div class="Hanoi-store">
              <p>Hà Nôi</p>
              <ul>
                <li>
                  <p>105/562 Đường Láng, Đống Đa, 69 Phố Vọng, Q. Hai Bà Trưng</p>
                  <p class="store-direct">Chỉ đường</p>
                </li>
                <li>
                  <p>69 Phố Vọng, Q. Hai Bà Trưng</p>
                  <p class="store-direct">Chỉ đường</p>
                </li>
              </ul>
            </div>
            <div class="HCM-store">
              <p>TP.Hồ Chí Minh</p>
              <ul>
                <li>
                  <p>62 Duy Tân, P. 15, Phú Nhuận</p>
                  <p class="store-direct">Chỉ đường</p>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div style="margin-bottom: 40px "></div>
      <div class="copyRight">
        <div class="copyRight__left">
          <p>Copyright (C) 2020 </p>
          <p>Công ty TNHH Công nghệ Think Việt Nam | Số ĐKKD 0107273909 do Sở KHĐT Thành phố Hà Nội cấp ngày
            30/12/2015</p>
        </div>
        <div class="copyRight__right">
          <img alt="certification" src="/img/certification.svg">
        </div>
      </div>
    </div>
  </div>

</template>

<script>

  export default {
    data() {
      return {
        res: [
          {
            "id": 20,
            "shared_url": "similique-corrupti-et-debitis-ipsa-dolorum-dolor-officiis-illo-dolor-id-maiores-ut.html",
            "title": "Xiaomi ra mắt máy tính để bàn all-in-one: Chip Intel thế hệ 9, màn hình 24 inch, giá từ 10.6 triệu đồng",
            "description": "Máy tính để bàn all-in-one Ningmei CR600 mới của Xiaomi có thiết kế đẹp mắt, cấu hình phần cứng mạnh mẽ nhưng đi kèm mức giá khá là phải chăng. ",
            "thumbnail": "https://genk.mediacdn.vn/139269124445442048/2020/2/15/5db66c102ebd4f818c6a9effe11b6bc5-15817454907481953928668.jpg",
            "category": {
              "id": 6,
              "name": "Game",
              "shared_url": "game"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 19,
            "shared_url": "quis-delectus-accusamus-perspiciatis-repudiandae-ex-quo-vitae-dolor-quo-mollitia-quia-ut-et-numquam.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://www.xtmobile.vn/vnt_upload/File/02_2019/thiet-ke-samsung-galaxy-s10-plus-xtmobile.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 18,
            "shared_url": "vero-nisi-ab-iste-sint-ut-doloremque-repellat-sit-molestias.html",
            "title": "Đây là cách virus Covid-19 tàn phá cơ thể",
            "description": "Về cơ bản, phổi của bệnh nhân sẽ cứng lại, ngập dịch và họ không còn thở được.",
            "thumbnail": "https://znews-photo.zadn.vn/w660/Uploaded/yqdlcqrwq/2020_02_27/Z17527022020.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 17,
            "shared_url": "et-ut-voluptatem-inventore-recusandae-in-voluptatem-suscipit-perferendis.html",
            "title": "Dừng thí điểm xe công nghệ, Grab sẽ hoạt động ra sao tại Việt Nam?",
            "description": "Từ 1/4, Bộ GTVT sẽ dừng hoạt động thí điểm xe công nghệ, nhiều người lo lắng cho số phận của các hãng gọi xe công nghệ như Grab, FastGo,... Tuy nhiên các hãng như Grab đã có chuẩn bị từ trước.",
            "thumbnail": "https://genk.mediacdn.vn/2018/8/9/macbook-pro-2018800x450-153375022066081190617.jpg",
            "category": {
              "id": 5,
              "name": "Gear",
              "shared_url": "gear"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 16,
            "shared_url": "at-consequuntur-aliquam-error-tenetur-laborum-earum-est-debitis-quia-eum-impedit-voluptas.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://hoanghamobile.com/tin-tuc/wp-content/uploads/2019/09/mua-appe-watch-series-3-1.jpg",
            "category": {
              "id": 1,
              "name": "Reviews",
              "shared_url": "reviews"
            },
            "created_by": {
              "id": 1,
              "name": "Hoàng",
              "shared_url": "hoang-1"
            },
            "created_at": "2020-05-16 19:11:25"
          }
        ],
        cate:[
          {
            "id": 1,
            "name": "Tin tức",
            "shared_url": "tin-tuc"
          },
          {
            "id": 2,
            "name": "Reviews",
            "shared_url": "reviews"
          },
          {
            "id": 3,
            "name": "Khuyến mãi",
            "shared_url": "khuyen-mai"
          },
          {
            "id": 4,
            "name": "Laptop",
            "shared_url": "laptop"
          },
          {
            "id": 5,
            "name": "Gear",
            "shared_url": "gear"
          },
          {
            "id": 6,
            "name": "Game",
            "shared_url": "game"
          },
          {
            "id": 7,
            "name": "Tuyển dụng",
            "shared_url": "tuyen-dung"
          },
          {
            "id": 8,
            "name": "Về ThinkPro",
            "shared_url": "ve-thinkpro"
          }
        ],
        page : 1 ,
        is_selected: 'tin-tuc'
      }
    },
    methods : {
      changeCate(value){
        value === 'tin-tuc' ?   this.res = [
          {
            "id": 20,
            "shared_url": "similique-corrupti-et-debitis-ipsa-dolorum-dolor-officiis-illo-dolor-id-maiores-ut.html",
            "title": "Xiaomi ra mắt máy tính để bàn all-in-one: Chip Intel thế hệ 9, màn hình 24 inch, giá từ 10.6 triệu đồng",
            "description": "Máy tính để bàn all-in-one Ningmei CR600 mới của Xiaomi có thiết kế đẹp mắt, cấu hình phần cứng mạnh mẽ nhưng đi kèm mức giá khá là phải chăng. ",
            "thumbnail": "https://genk.mediacdn.vn/139269124445442048/2020/2/15/5db66c102ebd4f818c6a9effe11b6bc5-15817454907481953928668.jpg",
            "category": {
              "id": 6,
              "name": "Game",
              "shared_url": "game"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 19,
            "shared_url": "quis-delectus-accusamus-perspiciatis-repudiandae-ex-quo-vitae-dolor-quo-mollitia-quia-ut-et-numquam.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://www.xtmobile.vn/vnt_upload/File/02_2019/thiet-ke-samsung-galaxy-s10-plus-xtmobile.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 18,
            "shared_url": "vero-nisi-ab-iste-sint-ut-doloremque-repellat-sit-molestias.html",
            "title": "Đây là cách virus Covid-19 tàn phá cơ thể",
            "description": "Về cơ bản, phổi của bệnh nhân sẽ cứng lại, ngập dịch và họ không còn thở được.",
            "thumbnail": "https://znews-photo.zadn.vn/w660/Uploaded/yqdlcqrwq/2020_02_27/Z17527022020.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 17,
            "shared_url": "et-ut-voluptatem-inventore-recusandae-in-voluptatem-suscipit-perferendis.html",
            "title": "Dừng thí điểm xe công nghệ, Grab sẽ hoạt động ra sao tại Việt Nam?",
            "description": "Từ 1/4, Bộ GTVT sẽ dừng hoạt động thí điểm xe công nghệ, nhiều người lo lắng cho số phận của các hãng gọi xe công nghệ như Grab, FastGo,... Tuy nhiên các hãng như Grab đã có chuẩn bị từ trước.",
            "thumbnail": "https://genk.mediacdn.vn/2018/8/9/macbook-pro-2018800x450-153375022066081190617.jpg",
            "category": {
              "id": 5,
              "name": "Gear",
              "shared_url": "gear"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 16,
            "shared_url": "at-consequuntur-aliquam-error-tenetur-laborum-earum-est-debitis-quia-eum-impedit-voluptas.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://hoanghamobile.com/tin-tuc/wp-content/uploads/2019/09/mua-appe-watch-series-3-1.jpg",
            "category": {
              "id": 1,
              "name": "Reviews",
              "shared_url": "reviews"
            },
            "created_by": {
              "id": 1,
              "name": "Hoàng",
              "shared_url": "hoang-1"
            },
            "created_at": "2020-05-16 19:11:25"
          }
        ] :this.res = [
          {
            "id": 20,
            "shared_url": "similique-corrupti-et-debitis-ipsa-dolorum-dolor-officiis-illo-dolor-id-maiores-ut.html",
            "title": "Xiaomi ra mắt máy tính để bàn all-in-one: Chip Intel thế hệ 9, màn hình 24 inch, giá từ 10.6 triệu đồng",
            "description": "Máy tính để bàn all-in-one Ningmei CR600 mới của Xiaomi có thiết kế đẹp mắt, cấu hình phần cứng mạnh mẽ nhưng đi kèm mức giá khá là phải chăng. ",
            "thumbnail": "https://hoanghamobile.com/Uploads/Originals/2019/09/17/201909171415023411_123.png;width=820;height=550;watermark=logo;crop=auto;format=jpg",
            "category": {
              "id": 6,
              "name": "Game",
              "shared_url": "game"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 19,
            "shared_url": "quis-delectus-accusamus-perspiciatis-repudiandae-ex-quo-vitae-dolor-quo-mollitia-quia-ut-et-numquam.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://image.thanhnien.vn/800/uploaded/nthanhluan/2020_05_09/mb2_kxyu.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 18,
            "shared_url": "vero-nisi-ab-iste-sint-ut-doloremque-repellat-sit-molestias.html",
            "title": "Đây là cách virus Covid-19 tàn phá cơ thể",
            "description": "Về cơ bản, phổi của bệnh nhân sẽ cứng lại, ngập dịch và họ không còn thở được.",
            "thumbnail": "https://cdn.tgdd.vn/Files/2020/02/05/1234448/nhung-diem-nang-cap-tren-macbook-pro-2020-thoi-diem-ra-mat-760x367.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 17,
            "shared_url": "et-ut-voluptatem-inventore-recusandae-in-voluptatem-suscipit-perferendis.html",
            "title": "Dừng thí điểm xe công nghệ, Grab sẽ hoạt động ra sao tại Việt Nam?",
            "description": "Từ 1/4, Bộ GTVT sẽ dừng hoạt động thí điểm xe công nghệ, nhiều người lo lắng cho số phận của các hãng gọi xe công nghệ như Grab, FastGo,... Tuy nhiên các hãng như Grab đã có chuẩn bị từ trước.",
            "thumbnail": "https://cdn.tgdd.vn/Files/2020/02/05/1234448/nhung-diem-nang-cap-tren-macbook-pro-2020-thoi-diem-ra-mat-1.jpg",
            "category": {
              "id": 5,
              "name": "Gear",
              "shared_url": "gear"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 16,
            "shared_url": "at-consequuntur-aliquam-error-tenetur-laborum-earum-est-debitis-quia-eum-impedit-voluptas.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://cellphones.com.vn/sforum/wp-content/uploads/2020/01/macbook-pro-16-icnh-01.jpg",
            "category": {
              "id": 1,
              "name": "Reviews",
              "shared_url": "reviews"
            },
            "created_by": {
              "id": 1,
              "name": "Hoàng",
              "shared_url": "hoang-1"
            },
            "created_at": "2020-05-16 19:11:25"
          }
        ]
        this.page = 1
        this.is_selected = value
        window.scroll({
          top: 0,
          left: 0,
          behavior: 'smooth'
        });
      },
      loadMore () {
        this.page ++
        let res = [
          {
            "id": 20,
            "shared_url": "similique-corrupti-et-debitis-ipsa-dolorum-dolor-officiis-illo-dolor-id-maiores-ut.html",
            "title": "Xiaomi ra mắt máy tính để bàn all-in-one: Chip Intel thế hệ 9, màn hình 24 inch, giá từ 10.6 triệu đồng",
            "description": "Máy tính để bàn all-in-one Ningmei CR600 mới của Xiaomi có thiết kế đẹp mắt, cấu hình phần cứng mạnh mẽ nhưng đi kèm mức giá khá là phải chăng. ",
            "thumbnail": "https://genk.mediacdn.vn/139269124445442048/2020/2/15/5db66c102ebd4f818c6a9effe11b6bc5-15817454907481953928668.jpg",
            "category": {
              "id": 6,
              "name": "Game",
              "shared_url": "game"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 19,
            "shared_url": "quis-delectus-accusamus-perspiciatis-repudiandae-ex-quo-vitae-dolor-quo-mollitia-quia-ut-et-numquam.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://www.xtmobile.vn/vnt_upload/File/02_2019/thiet-ke-samsung-galaxy-s10-plus-xtmobile.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 18,
            "shared_url": "vero-nisi-ab-iste-sint-ut-doloremque-repellat-sit-molestias.html",
            "title": "Đây là cách virus Covid-19 tàn phá cơ thể",
            "description": "Về cơ bản, phổi của bệnh nhân sẽ cứng lại, ngập dịch và họ không còn thở được.",
            "thumbnail": "https://znews-photo.zadn.vn/w660/Uploaded/yqdlcqrwq/2020_02_27/Z17527022020.jpg",
            "category": {
              "id": 3,
              "name": "Khuyến mãi",
              "shared_url": "khuyen-mai"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 17,
            "shared_url": "et-ut-voluptatem-inventore-recusandae-in-voluptatem-suscipit-perferendis.html",
            "title": "Dừng thí điểm xe công nghệ, Grab sẽ hoạt động ra sao tại Việt Nam?",
            "description": "Từ 1/4, Bộ GTVT sẽ dừng hoạt động thí điểm xe công nghệ, nhiều người lo lắng cho số phận của các hãng gọi xe công nghệ như Grab, FastGo,... Tuy nhiên các hãng như Grab đã có chuẩn bị từ trước.",
            "thumbnail": "https://genk.mediacdn.vn/2018/8/9/macbook-pro-2018800x450-153375022066081190617.jpg",
            "category": {
              "id": 5,
              "name": "Gear",
              "shared_url": "gear"
            },
            "created_by": {
              "id": 2,
              "name": "Admin",
              "shared_url": "admin-2"
            },
            "created_at": "2020-05-16 19:11:25"
          },
          {
            "id": 16,
            "shared_url": "at-consequuntur-aliquam-error-tenetur-laborum-earum-est-debitis-quia-eum-impedit-voluptas.html",
            "title": "Giới phân tích dự đoán Samsung có thể bán 32 triệu chiếc Galaxy S20 Series trong năm nay",
            "description": "Samsung gần đây đã giới thiệu dòng flagship Galaxy S20 series mới của mình, bao gồm Galaxy S20, S20 Pus...",
            "thumbnail": "https://hoanghamobile.com/tin-tuc/wp-content/uploads/2019/09/mua-appe-watch-series-3-1.jpg",
            "category": {
              "id": 1,
              "name": "Reviews",
              "shared_url": "reviews"
            },
            "created_by": {
              "id": 1,
              "name": "Hoàng",
              "shared_url": "hoang-1"
            },
            "created_at": "2020-05-16 19:11:25"
          }
        ]
        this.res = [ ...this.res , ...res]
      }
    }
  }
</script>

<style>
  * {
    padding: 0;
    margin: 0;
  }

  body {
    letter-spacing: -1px;
    font-size: 16px;
  }

  /*Header */
  .header {
    display: flex;
    height: 72px;
    border-bottom: 1px solid #E3E7EF;
    margin-left: 31px;
    position: sticky;
    top: 0;
    background-color: #fff;
  }

  .header__item {
    width: 10%;
  }

  .header_logo {
    display: flex;
    align-items: center;
  }

  .header_logo__icon {
    margin-right: 7px;
  }

  .header_logo__icon, header_logo__text {
    display: inline-block;
  }

  .header_nav {
    flex-grow: 1;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .header_nav__list {
    list-style-type: none;
  }

  .header_nav__list_item {
    display: inline-block;
    margin: 0 24px;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 24px;
    cursor: pointer;
  }

  .header_nav__item_selected {
    color: #06C1D4;
  }

  .header_login {
    display: flex;
    justify-content: flex-end;
  }

  .header_login img {
    margin-right: 40px;
  }

  /* End header*/

  .content {
    width: 1000px;
    margin: 0 auto;
  }

  .highLight-post__image img {
    max-height: 450px;
    width: 100%;
    object-fit: cover;
  }

  .highLight-post__info {
    margin-top: 20px;
    margin-bottom: 10px;
    font-size: 14px;
  }

  .highLight-post__type--space {
    margin-right: 1rem;
    font-weight: 600;
  }

  .highLight-post__author {
    color: #06C1D4;
  }

  .highLight-post__title {
    font-weight: bold;
    font-size: 32px;
    line-height: 40px;
    margin-bottom: 16px;
  }

  .highLight-post__detail {
    font-size: 18px;
    line-height: 28px;
    color: #414956;
  }

  /*  post Items*/
  .list-post {
    display: flex;
    margin-top: 40px;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .post-item-cover {
    width: 50%;
    max-height: 516px;
    overflow-x: hidden;
    margin-bottom: 16px;
    transition: 0.3s;
    cursor: pointer;
    padding: 16px;
  }

  .post-item-cover:hover {
    box-shadow: 0px 4px 24px rgba(0, 0, 0, 0.25);
  }

  .post-items {
    transition: 0.3s;
  }

  .post-items .highLight-post__image img {
    max-height: 220px;
  }

  .post-items .highLight-post__title {
    font-size: 24px;
    line-height: 32px;
  }

  .loadMore {
    display: flex;
    justify-content: center;
    margin-top: 30px;
    margin-bottom: 52px;
  }

  .loadMore__btn {
    display: inline-block;
    background-color: #06C1D4;
    border-radius: 52px;
    height: 52px;
    line-height: 52px;
    cursor: pointer;
  }

  .loadMore__btn span {
    margin: 0 111px;
    font-weight: 600;
    font-size: 18px;
    line-height: 28px;
  }

  /*Enc Content*/

  /*Footer*/

  .footer {
    background-color: #272E3C;
    color: #fff;
  }

  .footer-content {
    width: 63%;
    margin: 0 auto;
    display: flex;
    padding-top: 53px;
    justify-content: space-between;
  }

  /*Footer content left*/
  .footer-content-left {
    width: 57%;
  }

  .footer-left__logo {
    display: flex;
    align-items: center;
    margin-bottom: 45px;
  }

  .footer-left__logo-icon, .footer-left__logo-text {
    display: inline-block;
  }

  .footer-left__logo-icon {
    margin-right: 17px;
  }

  .footer-left__content {
    display: flex;
    justify-content: space-between;
  }

  .footer-left__content p {
    font-weight: 600;
    font-size: 18px;
    line-height: 28px;
    margin-bottom: 1rem;
  }

  .footer-left__content ul li {
    list-style-type: none;
    opacity: 0.7;
    line-height: 24px;
    margin-bottom: 4px;
  }

  .footer-left__content-product {
    width: 40%;
  }

  .footer-product__list {
    display: flex;
    justify-content: space-between;
  }

  /*End footer content left*/

  .footer-content-right {
    width: 33%;
  }

  .footer-content-right__contact {
    height: 79px;
    margin-bottom: 45px;
  }

  .footer-content-right__social {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .footer-content-right__social .phone {
    font-weight: 600;
    font-size: 24px;
    line-height: 32px;
  }

  .footer-content-right__social .social span {
    margin: 0 8px;
  }

  .footer-content-right ul li {
    list-style-type: none;
    margin-bottom: 16px;
  }

  .shop-system {
    font-weight: 600;
    font-size: 18px;
    line-height: 28px;
    margin-bottom: 24px;
  }

  .footer-content-right__store {
    display: flex;
    justify-content: space-between;
  }

  .footer-content-right__store > .Hanoi-store {
    width: 43%;
  }

  .Hanoi-store > p {
    font-weight: 600;
    line-height: 24px;
    margin-bottom: 8px;
  }

  .HCM-store > p {
    font-weight: 600;
    line-height: 24px;
    margin-bottom: 8px;
  }

  .store-direct {
    font-weight: 600;
    line-height: 24px;
    color: #06C1D4;
    margin-top: 8px;
  }

  .copyRight {
    display: flex;
    padding-bottom: 14px;
    width: 61%;
    margin: 0 auto;
    align-items: center;
    justify-content: space-between;
  }

  .copyRight p {
    font-size: 12px;
    line-height: 20px;
    opacity: 0.5;
  }
</style>
