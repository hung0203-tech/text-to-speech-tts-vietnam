<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Text-to-Speech Converter | TTS Việt Nam</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --primary: #00B14F;
            --secondary: #FFC107;
            --dark: #212121;
            --light: #F5F5F5;
        }
        
        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--light);
            color: var(--dark);
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, var(--primary) 0%, #009140 100%);
        }
        
        .voice-option:hover {
            transform: scale(1.03);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }
        
        .speech-area {
            min-height: 200px;
            border-left: 4px solid var(--primary);
        }
        
        #waveform {
            height: 100px;
            background-color: #f0f0f0;
            border-radius: 8px;
        }
        
        @media (max-width: 768px) {
            .flex-col-reverse {
                flex-direction: column-reverse !important;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="gradient-bg text-white shadow-lg">
        <div class="container mx-auto px-4 py-6">
            <div class="flex justify-between items-center">
                <div class="flex items-center">
                    <img src="https://placehold.co/40x40" alt="TTS Việt Nam logo - Green sound waves icon" class="mr-3">
                    <h1 class="text-2xl font-bold">TTS Việt Nam</h1>
                </div>
                <nav class="hidden md:block">
                    <ul class="flex space-x-6">
                        <li><a href="#" class="hover:text-yellow-200 transition">Trang chủ</a></li>
                        <li><a href="#" class="hover:text-yellow-200 transition">Giới thiệu</a></li>
                        <li><a href="#" class="hover:text-yellow-200 transition">Bảng giá</a></li>
                        <li><a href="#" class="hover:text-yellow-200 transition">Liên hệ</a></li>
                    </ul>
                </nav>
                <button class="md:hidden">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-4 py-8">
        <div class="text-center mb-12">
            <h2 class="text-3xl md:text-4xl font-bold mb-4">Chuyển văn bản thành giọng nói tự nhiên</h2>
            <p class="text-gray-600 max-w-2xl mx-auto">Công nghệ AI tổng hợp giọng nói tiên tiến với nhiều giọng đọc tiếng Việt tự nhiên, phù hợp cho video, audiobook và nhiều ứng dụng khác.</p>
        </div>

        <div class="flex flex-col lg:flex-row gap-8">
            <!-- Text Input Section -->
            <div class="flex-1 bg-white rounded-lg shadow-md overflow-hidden">
                <div class="p-6">
                    <h3 class="text-xl font-semibold mb-4">Nhập văn bản của bạn</h3>
                    <textarea id="textInput" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-500 mb-4" rows="8" placeholder="Nhập hoặc dán văn bản bạn muốn chuyển thành giọng nói tại đây..."></textarea>
                    
                    <div class="flex flex-wrap gap-2 mb-6">
                        <button id="clearBtn" class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg hover:bg-gray-300 transition">Xóa</button>
                        <button id="sampleBtn" class="px-4 py-2 bg-blue-100 text-blue-700 rounded-lg hover:bg-blue-200 transition">Văn bản mẫu</button>
                        <button id="checkBtn" class="px-4 py-2 bg-purple-100 text-purple-700 rounded-lg hover:bg-purple-200 transition">Kiểm tra chính tả</button>
                    </div>
                </div>
            </div>

            <!-- Voice Selection & Controls -->
            <div class="flex-1 bg-white rounded-lg shadow-md overflow-hidden">
                <div class="p-6">
                    <h3 class="text-xl font-semibold mb-4">Tùy chọn giọng đọc</h3>
                    
                    <div class="grid grid-cols-2 md:grid-cols-3 gap-4 mb-6">
                        <div class="voice-option p-4 border rounded-lg cursor-pointer transition" data-voice="male1">
                            <div class="flex items-center">
                                <img src="https://placehold.co/40x40" alt="Male voice avatar 1 - Vietnamese male with short hair" class="rounded-full mr-3">
                                <div>
                                    <h4 class="font-medium">Nam miền Bắc</h4>
                                    <p class="text-sm text-gray-500">Chuẩn</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="voice-option p-4 border rounded-lg cursor-pointer transition" data-voice="female1">
                            <div class="flex items-center">
                                <img src="https://placehold.co/40x40" alt="Female voice avatar 1 - Vietnamese woman with long hair" class="rounded-full mr-3">
                                <div>
                                    <h4 class="font-medium">Nữ miền Nam</h4>
                                    <p class="text-sm text-gray-500">Phổ biến</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="voice-option p-4 border rounded-lg cursor-pointer transition" data-voice="female2">
                            <div class="flex items-center">
                                <img src="https://placehold.co/40x40" alt="Female voice avatar 2 - Young Vietnamese woman smiling" class="rounded-full mr-3">
                                <div>
                                    <h4 class="font-medium">Nữ miền Bắc</h4>
                                    <p class="text-sm text-gray-500">Tin tức</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label for="speedControl" class="block mb-2 font-medium">Tốc độ đọc:</label>
                        <input type="range" id="speedControl" min="0.5" max="2" step="0.1" value="1" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <div class="flex justify-between text-sm text-gray-500 mt-1">
                            <span>Chậm</span>
                            <span>Bình thường</span>
                            <span>Nhanh</span>
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label for="pitchControl" class="block mb-2 font-medium">Độ cao giọng:</label>
                        <input type="range" id="pitchControl" min="0.8" max="1.2" step="0.05" value="1" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <div class="flex justify-between text-sm text-gray-500 mt-1">
                            <span>Trầm</span>
                            <span>Bình thường</span>
                            <span>Cao</span>
                        </div>
                    </div>
                    
                    <button id="previewBtn" class="w-full py-3 bg-yellow-400 text-gray-800 font-medium rounded-lg hover:bg-yellow-500 transition mb-4">
                        Nghe thử
                    </button>
                    
                    <div class="hidden" id="waveform"></div>
                    
                    <div class="flex gap-4 mt-6">
                        <button id="convertBtn" class="flex-1 py-3 gradient-bg text-white font-medium rounded-lg hover:opacity-90 transition">
                            Chuyển đổi
                        </button>
                        <button id="downloadBtn" class="flex-1 py-3 bg-gray-800 text-white font-medium rounded-lg hover:bg-gray-700 transition" disabled>
                            Tải xuống
                        </button>
                    </div>
                    
                    <div class="mt-4 text-sm text-gray-500">
                        <p><span class="font-medium">Lưu ý:</span> Bản miễn phí giới hạn 500 ký tự. Nâng cấp để chuyển đổi không giới hạn.</p>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Premium Section -->
    <section class="gradient-bg text-white py-12">
        <div class="container mx-auto px-4">
            <h2 class="text-2xl font-bold text-center mb-8">Nâng cấp tài khoản của bạn</h2>
            
            <div class="grid md:grid-cols-3 gap-8 max-w-5xl mx-auto">
                <div class="bg-white text-gray-800 rounded-lg shadow-lg overflow-hidden">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2">Cơ bản</h3>
                        <p class="text-gray-600 mb-4">Phù hợp cho cá nhân</p>
                        <div class="flex items-end mb-4">
                            <span class="text-4xl font-bold">99.000đ</span>
                            <span class="text-gray-500 ml-1">/tháng</span>
                        </div>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                50,000 ký tự/tháng
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                5 giọng đọc
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Tải xuống MP3
                            </li>
                        </ul>
                        <button class="w-full py-2 border-2 border-green-500 text-green-500 font-medium rounded-lg hover:bg-green-50 transition" onclick="showPaymentModal('basic')">
                            Chọn gói
                        </button>
                    </div>
                </div>
                
                <div class="bg-white text-gray-800 rounded-lg shadow-lg overflow-hidden transform scale-105 relative">
                    <div class="absolute top-0 right-0 bg-yellow-400 text-gray-800 px-3 py-1 text-sm font-bold rounded-bl-lg">
                        Phổ biến
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2">Chuyên nghiệp</h3>
                        <p class="text-gray-600 mb-4">Tối ưu cho doanh nghiệp nhỏ</p>
                        <div class="flex items-end mb-4">
                            <span class="text-4xl font-bold">299.000đ</span>
                            <span class="text-gray-500 ml-1">/tháng</span>
                        </div>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Không giới hạn ký tự
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                12 giọng đọc
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Đa định dạng (MP3, WAV)
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Hỗ trợ ưu tiên
                            </li>
                        </ul>
                        <button class="w-full py-2 gradient-bg text-white font-medium rounded-lg hover:opacity-90 transition" onclick="showPaymentModal('professional')">
                            Chọn gói
                        </button>
                    </div>
                </div>
                
                <div class="bg-white text-gray-800 rounded-lg shadow-lg overflow-hidden">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2">Doanh nghiệp</h3>
                        <p class="text-gray-600 mb-4">Giải pháp cao cấp</p>
                        <div class="text-gray-800 mb-4">
                            <span class="text-xl font-medium">Liên hệ</span>
                        </div>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Giải pháp tùy chỉnh
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Giọng đọc riêng
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                API tích hợp
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                                </svg>
                                Hỗ trợ 24/7
                            </li>
                        </ul>
                        <button class="w-full py-2 border-2 border-gray-800 text-gray-800 font-medium rounded-lg hover:bg-gray-100 transition">
                            Liên hệ
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Payment Modal -->
    <div id="paymentModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center hidden z-50">
        <div class="bg-white rounded-lg shadow-xl max-w-md w-full mx-4">
            <div class="p-6">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-xl font-bold">Thanh toán qua MoMo</h3>
                    <button onclick="closePaymentModal()" class="text-gray-500 hover:text-gray-700">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>
                
                <div class="mb-6">
                    <div class="bg-purple-100 rounded-lg p-4 mb-4">
                        <div class="flex justify-between items-center">
                            <h4 class="font-medium" id="planName">Gói Cơ bản</h4>
                            <span class="font-bold" id="planPrice">99.000đ</span>
                        </div>
                    </div>
                    
                    <div class="mb-4">
                        <label for="phoneNumber" class="block text-gray-700 mb-2">Số điện thoại MoMo</label>
                        <input type="tel" id="phoneNumber" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-500" placeholder="Nhập số điện thoại đã đăng ký MoMo">
                    </div>
                    
                    <img src="https://placehold.co/300x100" alt="QR code for MoMo payment - Purple background with white QR pattern and MoMo logo" class="w-full mb-4">
                    
                    <div class="text-sm text-gray-600 mb-4">
                        <p>Vui lòng mở ứng dụng MoMo và quét mã QR hoặc nhập số điện thoại để thanh toán.</p>
                    </div>
                </div>
                
                <button id="confirmPayment" class="w-full py-3 bg-purple-600 text-white font-medium rounded-lg hover:bg-purple-700 transition">
                    Xác nhận thanh toán
                </button>
            </div>
        </div>
    </div>

    <!-- Result Modal -->
    <div id="resultModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center hidden z-50">
        <div class="bg-white rounded-lg shadow-xl max-w-md w-full mx-4">
            <div class="p-6 text-center">
                <div class="flex justify-center mb-4">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-16 w-16 text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                </div>
                <h3 class="text-xl font-bold mb-2" id="resultTitle">Thanh toán thành công!</h3>
                <p class="text-gray-600 mb-6" id="resultMessage">Tài khoản của bạn đã được nâng cấp lên gói Cơ bản. Bạn có thể bắt đầu sử dụng dịch vụ ngay bây giờ.</p>
                <button onclick="closeResultModal()" class="w-full py-3 gradient-bg text-white font-medium rounded-lg hover:opacity-90 transition">
                    Đóng
                </button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8">
        <div class="container mx-auto px-4">
            <div class="grid md:grid-cols-4 gap-8">
                <div>
                    <h3 class="text-lg font-semibold mb-4">TTS Việt Nam</h3>
                    <p class="text-gray-400">Công nghệ tổng hợp giọng nói AI tiên tiến nhất dành cho tiếng Việt.</p>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Liên kết</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Trang chủ</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Bảng giá</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">API</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Blog</a></li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Hỗ trợ</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Câu hỏi thường gặp</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Hướng dẫn sử dụng</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Liên hệ</a></li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Theo dõi chúng tôi</h3>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-400 hover:text-white transition">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M22.675 0h-21.35c-.732 0-1.325.593-1.325 1.325v21.351c0 .731.593 1.324 1.325 1.324h11.495v-9.294h-3.128v-3.622h3.128v-2.671c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12v9.293h6.116c.73 0 1.323-.593 1.323-1.325v-21.35c0-.732-.593-1.325-1.325-1.325z"/>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
                            </svg>
                        </a>
                    </div>
                </div>
            </div>
            <div class="border-t border-gray-700 mt-8 pt-6 text-center text-gray-400">
                <p>© 2023 TTS Việt Nam. Bảo lưu mọi quyền.</p>
            </div>
        </div>
    </footer>

    <script>
        // Global variables
        let selectedVoice = 'female1';
        let audioFileUrl = null;
        
        // DOM Elements
        const textInput = document.getElementById('textInput');
        const clearBtn = document.getElementById('clearBtn');
        const sampleBtn = document.getElementById('sampleBtn');
        const checkBtn = document.getElementById('checkBtn');
        const voiceOptions = document.querySelectorAll('.voice-option');
        const speedControl = document.getElementById('speedControl');
        const pitchControl = document.getElementById('pitchControl');
        const previewBtn = document.getElementById('previewBtn');
        const convertBtn = document.getElementById('convertBtn');
        const downloadBtn = document.getElementById('downloadBtn');
        const waveform = document.getElementById('waveform');
        const paymentModal = document.getElementById('paymentModal');
        const resultModal = document.getElementById('resultModal');
        const confirmPayment = document.getElementById('confirmPayment');
        const planName = document.getElementById('planName');
        const planPrice = document.getElementById('planPrice');
        const phoneNumber = document.getElementById('phoneNumber');
        
        // Event Listeners
        clearBtn.addEventListener('click', clearText);
        sampleBtn.addEventListener('click', insertSampleText);
        checkBtn.addEventListener('click', checkSpelling);
        previewBtn.addEventListener('click', previewSpeech);
        convertBtn.addEventListener('click', convertTextToSpeech);
        downloadBtn.addEventListener('click', downloadAudioFile);
        
        voiceOptions.forEach(option => {
            option.addEventListener('click', function() {
                voiceOptions.forEach(opt => opt.classList.remove('border-green-500', 'bg-green-50'));
                this.classList.add('border-green-500', 'bg-green-50');
                selectedVoice = this.getAttribute('data-voice');
            });
        });
        
        confirmPayment.addEventListener('click', processPayment);
        
        // Functions
        function clearText() {
            textInput.value = '';
        }
        
        function insertSampleText() {
            textInput.value = "Xin chào và chào mừng bạn đến với dịch vụ chuyển văn bản thành giọng nói của chúng tôi. Công nghệ AI tiên tiến giúp tạo ra giọng nói tự nhiên nhất từ văn bản tiếng Việt. Bạn có thể nghe thử ngay bây giờ hoặc chuyển đổi để tải về máy.";
        }
        
        function checkSpelling() {
            alert("Tính năng kiểm tra chính tả sẽ được kích hoạt trong phiên bản sau!");
        }
        
        function previewSpeech() {
            const text = textInput.value.trim();
            
            if (!text) {
                alert("Vui lòng nhập văn bản để nghe thử");
                return;
            }
            
            // Simulate preview with alert in this demo
            alert(`Đang phát giọng ${selectedVoice}: "${text.substring(0, 50)}..."\n\nTính năng đầy đủ sẽ có khi tích hợp với API TTS thực tế.`);
            
            // In a real implementation, we would call a TTS API here
            // and visualize the waveform when the audio plays
            waveform.classList.remove('hidden');
        }
        
        function convertTextToSpeech() {
            const text = textInput.value.trim();
            
            if (!text) {
                alert("Vui lòng nhập văn bản để chuyển đổi");
                return;
            }
            
            if (text.length > 500) {
                alert("Bản miễn phí giới hạn 500 ký tự. Vui lòng nâng cấp để chuyển đổi văn bản dài hơn.");
                return;
            }
            
            // Simulate conversion
            alert(`Đang chuyển đổi "${text.substring(0, 50)}..." sang giọng ${selectedVoice}.\n\nTính năng đầy đủ sẽ có khi tích hợp với API TTS thực tế.`);
            
            // In a real implementation, we would call a TTS API here
            // and get back an audio file URL
            audioFileUrl = "https://example.com/tts-output.mp3"; // This would be the actual URL from the API
            
            // Enable download button
            downloadBtn.disabled = false;
            downloadBtn.classList.remove('bg-gray-800');
            downloadBtn.classList.add('gradient-bg');
        }
        
        function downloadAudioFile() {
            if (!audioFileUrl) {
                alert("Không có file âm thanh để tải xuống");
                return;
            }
            
            // Create a temporary link and trigger download
            const a = document.createElement('a');
            a.href = audioFileUrl;
            a.download = 'audio-output.mp3';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            
            alert("File âm thanh đang được tải xuống. Trong phiên bản thực tế, đây sẽ là file MP3 thực sự được tạo từ API.");
        }
        
        function showPaymentModal(plan) {
            if (plan === 'basic') {
                planName.textContent = "Gói Cơ bản";
                planPrice.textContent = "99.000đ";
            } else {
                planName.textContent = "Gói Chuyên nghiệp";
                planPrice.textContent = "299.000đ";
            }
            
            paymentModal.classList.remove('hidden');
        }
        
        function closePaymentModal() {
            paymentModal.classList.add('hidden');
        }
        
        function processPayment() {
            const phone = phoneNumber.value.trim();
            
            if (!phone || !/^\d{10}$/.test(phone)) {
                alert("Vui lòng nhập số điện thoại MoMo hợp lệ!");
                return;
            }
            
            // Simulate payment processing
            setTimeout(() => {
                closePaymentModal();
                showResultModal(true);
            }, 1500);
        }
        
        function showResultModal(success) {
            const title = document.getElementById('resultTitle');
            const message = document.getElementById('resultMessage');
            
            if (success) {
                title.textContent = "Thanh toán thành công!";
                message.textContent = phoneNumber.value + " đã thanh toán thành công. Tài khoản của bạn đã được nâng cấp.";
            } else {
                title.textContent = "Thanh toán không thành công";
                message.textContent = "Đã có lỗi xảy ra trong quá trình thanh toán. Vui lòng thử lại hoặc liên hệ hỗ trợ.";
            }
            
            resultModal.classList.remove('hidden');
        }
        
        function closeResultModal() {
            resultModal.classList.add('hidden');
            
            if (phoneNumber.value) {
                // Reset form if payment was successful
                phoneNumber.value = '';
            }
        }
        
        // Initialize first voice option as selected
        document.querySelector('.voice-option[data-voice="female1"]').classList.add('border-green-500', 'bg-green-50');
    </script>
</body>
</html>
