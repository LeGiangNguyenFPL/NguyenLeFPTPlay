# NguyenLeFPTPlay
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chương Trình Thi Đua Nội Bộ - Cập Nhật Giải Thưởng</title>
    <style>
        /* Reset và cơ bản */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f4f4f4;
        }

        /* Top Banner Slider */
        .banner-slider {
            position: relative;
            width: 100%;
            height: 400px;
            overflow: hidden;
            margin-bottom: 20px;
        }
        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }
        .slide.active {
            opacity: 1;
        }
        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .slide-text {
            position: absolute;
            bottom: 20px;
            left: 20px;
            color: white;
            background: rgba(0,0,0,0.5);
            padding: 10px;
            border-radius: 5px;
        }

        /* Navigation Menu - Góc phải */
        .nav-menu {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
        }
        .nav-menu ul {
            list-style: none;
            background: #007bff;
            border-radius: 5px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
        }
        .nav-menu li {
            padding: 10px 15px;
        }
        .nav-menu a {
            color: white;
            text-decoration: none;
            display: block;
        }
        .nav-menu a:hover {
            background: #0056b3;
            border-radius: 3px;
        }

        /* Nội dung chính */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        h1 {
            text-align: center;
            margin-bottom: 30px;
            color: #007bff;
        }

        /* 4 Hạng Mục Giải Thưởng */
        .awards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }
        .award-category {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            text-align: center;
        }
        .award-category h3 {
            color: #007bff;
            margin-bottom: 10px;
        }
        .award-category p {
            color: #666;
        }
        .award-category .update-btn {
            background: #28a745;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 10px;
        }
        .award-category .update-btn:hover {
            background: #218838;
        }

        /* Trang Giải Thưởng (ẩn mặc định) */
        .awards-intro {
            display: none;
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        .awards-intro.active {
            display: block;
        }
        .awards-intro h2 {
            text-align: center;
            margin-bottom: 20px;
            color: #007bff;
        }
        .awards-intro ul {
            list-style: disc;
            padding-left: 20px;
        }
        .awards-intro li {
            margin-bottom: 10px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .banner-slider {
                height: 250px;
            }
            .nav-menu {
                top: 10px;
                right: 10px;
            }
            .nav-menu li {
                padding: 8px 10px;
            }
        }
    </style>
</head>
<body>

    <!-- Navigation Menu - Góc phải -->
    <nav class="nav-menu">
        <ul>
            <li><a href="#" onclick="showHome()">Trang Chủ</a></li>
            <li><a href="#" onclick="showAwards()">Giải Thưởng</a></li>
        </ul>
    </nav>

    <!-- Top Banner Slider -->
    <div class="banner-slider">
        <div class="slide active">
            <img src="https://via.placeholder.com/1200x400/007bff/white?text=Slide+1+-+Chao+mung+den+voi+chuong+trinh" alt="Slide 1">
            <div class="slide-text">
                <h2>Slide 1: Giới thiệu chương trình</h2>
                <p>Chào mừng các bạn tham gia thi đua nội bộ!</p>
            </div>
        </div>
        <div class="slide">
            <img src="https://via.placeholder.com/1200x400/28a745/white?text=Slide+2+-+Muc+tieu" alt="Slide 2">
            <div class="slide-text">
                <h2>Slide 2: Mục tiêu</h2>
                <p>Đạt được thành tích cao nhất trong năm.</p>
            </div>
        </div>
        <div class="slide">
            <img src="https://via.placeholder.com/1200x400/ff6b6b/white?text=Slide+3+-+Giai+thuong" alt="Slide 3">
            <div class="slide-text">
                <h2>Slide 3: Giải thưởng hấp dẫn</h2>
                <p>Các hạng mục giải thưởng đang chờ bạn!</p>
            </div>
        </div>
    </div>

    <div class="container">
        <!-- Trang Chủ: Cập Nhật Thông Tin Giải (mặc định hiển thị) -->
        <div id="home-page" class="active">
            <h1>Cập Nhật Giải Thưởng - Chương Trình Thi Đua Nội Bộ</h1>
            <p style="text-align: center; margin-bottom: 30px;">Dưới đây là 4 hạng mục giải thưởng chính. Bạn có thể cập nhật thông tin chi tiết cho từng hạng mục.</p>
            
            <div class="awards-grid">
                <div class="award-category">
                    <h3>Hạng Mục 1: Giải Vàng</h3>
                    <p>Mô tả: Giải thưởng cao nhất cho cá nhân xuất sắc.</p>
                    <p>Số lượng: 5 người</p>
                    <button class="update-btn" onclick="updateAward(1)">Cập Nhật</button>
                </div>
                <div class="award-category">
                    <h3>Hạng Mục 2: Giải Bạc</h3>
                    <p>Mô tả: Giải thưởng cho nhóm xuất sắc.</p>
                    <p>Số lượng: 10 nhóm</p>
                    <button class="update-btn" onclick="updateAward(2)">Cập Nhật</button>
                </div>
                <div class="award-category">
                    <h3>Hạng Mục 3: Giải Đồng</h3>
                    <p>Mô tả: Giải thưởng khuyến khích cá nhân.</p>
                    <p>Số lượng: 20 người</p>
                    <button class="update-btn" onclick="updateAward(3)">Cập Nhật</button>
                </div>
                <div class="award-category">
                    <h3>Hạng Mục 4: Giải Đặc Biệt</h3>
                    <p>Mô tả: Giải thưởng sáng tạo đột phá.</p>
                    <p>Số lượng: 3 người</p>
                    <button class="update-btn" onclick="updateAward(4)">Cập Nhật</button>
                </div>
            </div>
        </div>

        <!-- Menu Giải Thưởng: Giới Thiệu Hệ Thống Giải -->
        <div id="awards-page" class="awards-intro">
            <h2>Giới Thiệu Hệ Thống Giải Thưởng</h2>
            <p>Hệ thống giải thưởng được thiết kế để khuyến khích và ghi nhận đóng góp của các thành viên trong chương trình thi đua nội bộ. Các hạng mục bao gồm:</p>
            <ul>
                <li><strong>Giải Vàng:</strong> Dành cho cá nhân có thành tích vượt trội, phần thưởng: 10 triệu VND + chứng nhận.</li>
                <li><strong>Giải Bạc:</strong> Dành cho nhóm có dự án xuất sắc, phần thưởng: 5 triệu VND/nhóm + chứng nhận.</li>
                <li><strong>Giải Đồng:</strong> Khuyến khích cá nhân nỗ lực, phần thưởng: 2 triệu VND + chứng nhận.</li>
                <li><strong>Giải Đặc Biệt:</strong> Sáng tạo đột phá, phần thưởng: 15 triệu VND + cơ hội thăng tiến.</li>
            </ul>
            <p>Để cập nhật hoặc tham gia, vui lòng liên hệ ban tổ chức.</p>
        </div>
    </div>

    <script>
        // Slider cho Banner
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;

        function nextSlide() {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + 1) % totalSlides;
            slides[currentSlide].classList.add('active');
        }

        setInterval(nextSlide, 3000); // Tự động chuyển slide sau 3 giây

        // Chuyển đổi giữa Trang Chủ và Giải Thưởng
        function showHome() {
            document.getElementById('home-page').style.display = 'block';
            document.getElementById('awards-page').style.display = 'none';
        }

        function showAwards() {
            document.getElementById('home-page').style.display = 'none';
            document.getElementById('awards-page').style.display = 'block';
        }

        // Hàm cập nhật giải thưởng (placeholder - bạn có thể mở rộng thành form cập nhật)
        function updateAward(category) {
            alert(`Đang cập nhật hạng mục ${category}. Bạn có thể thêm form nhập liệu ở đây!`);
        }
    </script>

</body>
</html>
