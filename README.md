<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>الأولى البصرية للسيارات والاقساط</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Tajawal', sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            padding: 20px;
            color: #333;
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        
        .header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            font-weight: 900;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .cars-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .car-card {
            display: flex;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        
        .car-card:hover {
            transform: translateY(-5px);
        }
        
        .car-image {
            flex: 0 0 120px;
            background-color: #eee;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #999;
            font-size: 14px;
        }
        
        .car-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .car-details {
            flex: 1;
            padding: 15px;
            position: relative;
        }
        
        .car-model {
            font-weight: 700;
            font-size: 1.2rem;
            color: #1e3c72;
            margin-bottom: 5px;
        }
        
        .car-year {
            display: inline-block;
            background-color: #f0f0f0;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
            margin-right: 5px;
        }
        
        .car-price {
            margin: 8px 0;
            font-weight: 700;
            color: #2a5298;
        }
        
        .car-installment {
            background-color: #f8f9fa;
            padding: 8px;
            border-radius: 6px;
            margin: 8px 0;
            display: flex;
            justify-content: space-between;
        }
        
        .installment-amount {
            font-weight: 700;
            color: #e74c3c;
        }
        
        .car-plate {
            position: absolute;
            top: 15px;
            left: 15px;
            background-color: #27ae60;
            color: white;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
        }
        
        .contact-section {
            margin-top: 40px;
            background: linear-gradient(135deg, #27ae60, #2ecc71);
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        
        .contact-section h2 {
            margin-bottom: 15px;
            font-weight: 700;
        }
        
        .phone-numbers {
            font-size: 1.2rem;
            margin-bottom: 15px;
            direction: ltr;
            display: inline-block;
        }
        
        .address {
            margin-top: 15px;
            font-size: 0.9rem;
        }
        
        @media (max-width: 480px) {
            .header h1 {
                font-size: 1.8rem;
            }
            
            .car-card {
                flex-direction: column;
            }
            
            .car-image {
                flex: 0 0 150px;
            }
            
            .car-plate {
                top: 165px;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>الأولى البصرية للسيارات والاقساط</h1>
    </div>
    
    <div class="cars-container">
        <!-- السيارات من الجدول الأول -->
        <div class="car-card">
            <div class="car-image">
                <!-- هنا يمكنك إضافة صورة السيارة -->
                <span>صورة النترا الجديد</span>
            </div>
            <div class="car-details">
                <div class="car-model">النترا الجديد <span class="car-year">2024</span></div>
                <div class="car-price">مبلغ السيارة: 36,500,000</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">821,000</span>
                </div>
                <div class="car-duration">المدة: سنوات</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
        
        <div class="car-card">
            <div class="car-image">
                <span>صورة النترا الجديد</span>
            </div>
            <div class="car-details">
                <div class="car-model">النترا الجديد <span class="car-year">2025</span></div>
                <div class="car-price">مبلغ السيارة: 37,000,000</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">833,000</span>
                </div>
                <div class="car-duration">المدة: سنوات</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
        
        <div class="car-card">
            <div class="car-image">
                <span>صورة النترا الجديدة</span>
            </div>
            <div class="car-details">
                <div class="car-model">النترا الجديدة <span class="car-year">2023</span></div>
                <div class="car-price">مبلغ السيارة: 31,500,000</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">709,000</span>
                </div>
                <div class="car-duration">المدة: سنوات</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
        
        <!-- يمكنك إضافة المزيد من السيارات بنفس الطريقة -->
        <!-- سأضيف بعض الأمثلة الإضافية -->
        
        <div class="car-card">
            <div class="car-image">
                <span>صورة كيا سورنتوا</span>
            </div>
            <div class="car-details">
                <div class="car-model">كيا سورنتوا <span class="car-year">2025</span></div>
                <div class="car-price">مبلغ السيارة: 57,000,000</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">1,125,000</span>
                </div>
                <div class="car-duration">المدة: مقدم 7مليون كسنوات</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
        
        <div class="car-card">
            <div class="car-image">
                <span>صورة توبوتا بيك اب</span>
            </div>
            <div class="car-details">
                <div class="car-model">توبوتا بيك اب عالي نوفر <span class="car-year">2025</span></div>
                <div class="car-price">مبلغ السيارة: 60,000,000</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">1,125,000</span>
                </div>
                <div class="car-duration">المدة: مقدم 10مليون كسنوات</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
        
        <!-- السيارات من الجدول الثاني -->
        <div class="car-card">
            <div class="car-image">
                <span>صورة كوراك هابود</span>
            </div>
            <div class="car-details">
                <div class="car-model">كوراك هابود وارد خليجي</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">455,000</span>
                </div>
                <div class="car-duration">المدة: سنوات 8</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
        
        <div class="car-card">
            <div class="car-image">
                <span>صورة MINI EV</span>
            </div>
            <div class="car-details">
                <div class="car-model">MINI EV</div>
                <div class="car-installment">
                    <span>القسط:</span>
                    <span class="installment-amount">178,000</span>
                </div>
                <div class="car-duration">المدة: سنوات 8</div>
                <div class="car-plate">مع اللوحة</div>
            </div>
        </div>
    </div>
    
    <div class="contact-section">
        <h2>التواصل والاستفسار</h2>
        <div class="phone-numbers">07717000039 - 07817000039</div>
        <div>او زورونا</div>
        <div class="address">دور النقط قرب القمر المنبر مقابل ملعب البلديات</div>
    </div>
</body>
</html>
