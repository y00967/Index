<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة المحامي اليمني - الاستشارات القانونية والوساطة</title>
    <!-- استيراد خط وتنسيقات Tailwind CSS لتصميم فخم وسريع -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap');
        body { font-family: 'Cairo', sans-serif; }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">

    <!-- رأس الصفحة -->
    <header class="bg-blue-900 text-white shadow-md">
        <div class="container mx-auto px-6 py-4 flex justify-between items-center">
            <h1 class="text-2xl font-bold">⚖️ منصة المحامي اليمني</h1>
            <nav class="hidden md:flex space-x-6 space-x-reverse">
                <a href="#lawyers" class="hover:text-blue-300">ابحث عن محامٍ</a>
                <a href="#services" class="hover:text-blue-300">الخدمات</a>
                <a href="#contact" class="hover:text-blue-300">اتصل بنا</a>
            </nav>
        </div>
    </header>

    <!-- القسم الرئيسي -->
    <section class="bg-blue-800 text-white py-16 text-center">
        <div class="container mx-auto px-6">
            <h2 class="text-4xl font-bold mb-4">استشر نخبة من المحامين المعتمدين في اليمن</h2>
            <p class="text-lg text-blue-200 mb-8">احصل على استشارة قانونية موثوقة بكل سهولة وأمان تام.</p>
            <a href="#lawyers" class="bg-amber-500 hover:bg-amber-600 text-white font-bold py-3 px-8 rounded-lg shadow-lg">احجز استشارتك الآن</a>
        </div>
    </section>

    <!-- قائمة المحامين ونظام الحجز والدفع -->
    <main id="lawyers" class="container mx-auto px-6 py-12">
        <h3 class="text-2xl font-bold mb-8 text-center text-blue-900">المحامون المتاحون حالياً</h3>
        
        <div class="grid md:grid-cols-2 gap-8">
            
            <!-- بطاقة محامي (مثال) -->
            <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100 flex flex-col justify-between">
                <div>
                    <div class="flex items-center space-x-4 space-x-reverse mb-4">
                        <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center text-blue-800 text-2xl font-bold">أ</div>
                        <div>
                            <h4 class="text-xl font-bold">أ. أحمد الصهباني</h4>
                            <p class="text-gray-500 text-sm">مستشار قانوني ومحامٍ تجاري</p>
                        </div>
                    </div>
                    <p class="text-gray-600 mb-4 text-sm">خبرة واسعة في قضايا الشركات، العقود التجارية، وقضايا الأحوال الشخصية في صنعاء وجميع المحاكم اليمنية.</p>
                    <div class="text-blue-900 font-bold mb-4">رسوم الاستشارة: 5,000 ريال يمني</div>
                </div>

                <button onclick="openCheckout('أ. أحمد الصهباني', 5000)" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 rounded-lg font-bold transition">
                    اختر المحامي وحجز استشارة
                </button>
            </div>

            <!-- بطاقة محامي أخرى (مثال) -->
            <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100 flex flex-col justify-between">
                <div>
                    <div class="flex items-center space-x-4 space-x-reverse mb-4">
                        <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center text-blue-800 text-2xl font-bold">م</div>
                        <div>
                            <h4 class="text-xl font-bold">أ. مراد العريقي</h4>
                            <p class="text-gray-500 text-sm">مختص بالقضايا الجنائية والمدنية</p>
                        </div>
                    </div>
                    <p class="text-gray-600 mb-4 text-sm">تقديم المرافعات، صياغة المذكرات القانونية، وحل النزاعات وفض العمالة بمهنية عالية.</p>
                    <div class="text-blue-900 font-bold mb-4">رسوم الاستشارة: 7,000 ريال يمني</div>
                </div>

                <button onclick="openCheckout('أ. مراد العريقي', 7000)" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 rounded-lg font-bold transition">
                    اختر المحامي وحجز استشارة
                </button>
            </div>

        </div>
    </main>

    <!-- نافذة الدفع وإتمام الحجز (مودال مخفي افتراضياً) -->
    <div id="checkoutModal" class="fixed inset-0 bg-black bg-opacity-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-xl max-w-md w-full p-6 relative shadow-2xl">
            <button onclick="closeCheckout()" class="absolute top-4 left-4 text-gray-400 hover:text-gray-600 text-xl font-bold">&times;</button>
            
            <h3 class="text-xl font-bold mb-2 text-blue-900">إتمام الدفع وحجز الاستشارة</h3>
            <p id="modalLawyerInfo" class="text-gray-600 text-sm mb-4"></p>

            <form id="paymentForm" onsubmit="submitPayment(event)">
                <div class="mb-4">
                    <label class="block text-sm font-medium mb-1">اسم العميل:</label>
                    <input type="text" id="clientName" required class="w-full border border-gray-300 p-2 rounded-lg focus:outline-none focus:border-blue-500" placeholder="أدخل اسمك الثلاثي">
                </div>

                <div class="mb-4">
                    <label class="block text-sm font-medium mb-1">رقم الهاتف (واتساب):</label>
                    <input type="tel" id="clientPhone" required class="w-full border border-gray-300 p-2 rounded-lg focus:outline-none focus:border-blue-500" placeholder="77xxxxxxx أو 73xxxxxxx">
                </div>

                <div class="mb-4">
                    <label class="block text-sm font-medium mb-1">اختر بنك أو شبكة التحويل اليمنية:</label>
                    <select id="bankName" class="w-full border border-gray-300 p-2 rounded-lg focus:outline-none focus:border-blue-500">
                        <option value="Kuraimi">بنك الكريمي (الكريمي فلوس / موبايل موني)</option>
                        <option value="Tadamon">بنك التضامن</option>
                        <option value="Jawifi">شبكة الحازمي للصرافة</option>
                        <option value="MobilyMoney">يمن موبايل - موني</option>
                    </select>
                </div>

                <div class="mb-4">
                    <label class="block text-sm font-medium mb-1">رقم سند الحوالة أو إيصال الدفع:</label>
                    <input type="text" id="transferNumber" required class="w-full border border-gray-300 p-2 rounded-lg focus:outline-none focus:border-blue-500" placeholder="أدخل رقم الإيصال أو الحوالة البنكية بدقة">
                </div>

                <button type="submit" class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-2 rounded-lg transition">
                    تأكيد وإرسال بيانات الحوالة
                </button>
            </form>

            <div id="successMessage" class="hidden mt-4 p-4 bg-green-100 text-green-800 rounded-lg text-center font-bold">
                تم إرسال طلبك بنجاح! سيتم مراجعة رقم الحوالة وتفعيل الجلسة خلال دقائق.
            </div>
        </div>
    </div>

    <!-- تذييل الصفحة -->
    <footer class="bg-gray-800 text-white text-center py-6 mt-12">
        <p>جميع الحقوق محفوظة © 2026 - منصة المحامي اليمني</p>
    </footer>

    <!-- أكواد الجافاسكريبت للتحكم بالصفحة والنافذة -->
    <script>
        let selectedLawyerName = '';
        let selectedFee = 0;

        function openCheckout(lawyerName, fee) {
            selectedLawyerName = lawyerName;
            selectedFee = fee;
            document.getElementById('modalLawyerInfo').innerHTML = `المحامي: <strong>${lawyerName}</strong><br>المبلغ المطلوب تحويله: <span class="text-blue-600 font-bold">${fee} ريال يمني</span>`;
            document.getElementById('checkoutModal').classList.remove('hidden');
            document.getElementById('successMessage').classList.add('hidden');
            document.getElementById('paymentForm').classList.remove('hidden');
        }

        function closeCheckout() {
            document.getElementById('checkoutModal').classList.add('hidden');
        }

        function submitPayment(e) {
            e.preventDefault();
            const clientName = document.getElementById('clientName').value;
            const transferNumber = document.getElementById('transferNumber').value;
            
            // هنا يمكنك ربط البيانات بقاعدة بيانات أو إرسالها عبر API
            console.log({
                lawyer: selectedLawyerName,
                fee: selectedFee,
                client: clientName,
                transferNumber: transferNumber
            });

            // إظهار رسالة النجاح وإخفاء الفورم مؤقتاً
            document.getElementById('paymentForm').classList.add('hidden');
            document.getElementById('successMessage').classList.remove('hidden');
            
            setTimeout(() => {
                closeCheckout();
            }, 4000);
        }
    </script>
</body>
</html>
 Index
بسم الله
