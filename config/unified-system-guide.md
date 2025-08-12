# دليل النظام الموحد للأنشطة التعليمية
# Unified Educational Activities System Guide

## نظرة عامة (Overview)

تم إنشاء نظام موحد لتطوير وتحسين جميع الأنشطة التعليمية في التطبيق. يشمل هذا النظام:

- **نظام ألوان عماني موحد** مع خصائص CSS متقدمة
- **مكتبة JavaScript شاملة** للوظائف المشتركة
- **تصميم متجاوب** يدعم جميع أحجام الشاشات
- **ميزات إمكانية الوصول** المتقدمة
- **نظام إدارة الأصوات** والحركات

## الملفات المطلوبة (Required Files)

### 1. القالب الموحد للتنسيقات (CSS Template)
```
config/unified-styles-template.css
```

### 2. مكتبة JavaScript الموحدة (JavaScript Library)
```
config/unified-scripts-template.js
```

## كيفية تطبيق النظام الموحد (How to Apply the Unified System)

### الخطوة 1: تحديث HTML الأساسي

في كل ملف نشاط، قم بتحديث قسم `<head>` ليشمل:

```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>اسم النشاط</title>
  
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">
  
  <!-- Unified Styles -->
  <link rel="stylesheet" href="../config/unified-styles-template.css">
  
  <!-- Activity-specific styles (optional) -->
  <style>
    /* إضافات خاصة بالنشاط هنا */
  </style>
</head>
```

### الخطوة 2: إضافة مكتبة JavaScript

قبل إغلاق `</body>`:

```html
  <!-- Unified Scripts -->
  <script src="../config/unified-scripts-template.js"></script>
  
  <!-- Activity-specific scripts -->
  <script>
    // الكود الخاص بالنشاط هنا
  </script>
</body>
</html>
```

### الخطوة 3: تطبيق الهيكل الموحد

استخدم الهيكل التالي في جسم الصفحة:

```html
<body>
  <!-- Skip link for accessibility -->
  <a href="#main-content" class="sr-only">تخطي إلى المحتوى الرئيسي</a>
  
  <!-- Main container -->
  <div class="container">
    <!-- Header -->
    <header class="header">
      <h1>عنوان النشاط</h1>
      <p>وصف النشاط</p>
    </header>
    
    <!-- Main content -->
    <main id="main-content">
      <!-- محتوى النشاط هنا -->
    </main>
  </div>
  
  <!-- Control buttons will be added automatically by JavaScript -->
</body>
```

## الفئات المتاحة (Available Classes)

### الأزرار (Buttons)
```html
<button class="btn btn-primary">زر أساسي</button>
<button class="btn btn-secondary">زر ثانوي</button>
<button class="btn btn-accent">زر مميز</button>
<button class="btn btn-outline">زر محدد</button>
<button class="btn btn-large">زر كبير</button>
<button class="btn btn-small">زر صغير</button>
```

### البطاقات (Cards)
```html
<div class="card">
  <h3>عنوان البطاقة</h3>
  <p>محتوى البطاقة</p>
</div>
```

### الشبكات (Grids)
```html
<div class="grid grid-2">
  <!-- عمودين متجاوبين -->
</div>

<div class="grid grid-3">
  <!-- ثلاثة أعمدة متجاوبة -->
</div>

<div class="grid grid-4">
  <!-- أربعة أعمدة متجاوبة -->
</div>
```

### عناصر النماذج (Form Elements)
```html
<div class="form-group">
  <label class="form-label">التسمية</label>
  <input type="text" class="form-input" placeholder="النص">
</div>

<div class="form-group">
  <label class="form-label">الاختيار</label>
  <select class="form-select">
    <option>خيار 1</option>
    <option>خيار 2</option>
  </select>
</div>
```

### الشاشات الخاصة (Special Displays)
```html
<!-- شاشة المؤقت -->
<div class="timer-display">00:30</div>

<!-- شاشة النقاط -->
<div class="score-display">25</div>

<!-- شريط التقدم -->
<div class="progress-bar">
  <div class="progress-fill" style="width: 60%"></div>
</div>
```

## وظائف JavaScript المتاحة (Available JavaScript Functions)

### التهيئة (Initialization)
```javascript
// التهيئة التلقائية تتم عند تحميل الصفحة
// يمكن الوصول للأدوات عبر ActivityUtils
```

### الأصوات (Sounds)
```javascript
// تشغيل صوت
ActivityUtils.playSound('click');
ActivityUtils.playSound('success');
ActivityUtils.playSound('error');

// تحكم في الأصوات
AppConfig.sounds.enabled = true; // تفعيل/إيقاف
AppConfig.sounds.volume = 0.7;   // مستوى الصوت
```

### الإشعارات (Notifications)
```javascript
// إظهار إشعار
ActivityUtils.showNotification('رسالة النجاح', 'success');
ActivityUtils.showNotification('رسالة خطأ', 'error');
ActivityUtils.showNotification('رسالة تحذير', 'warning');
ActivityUtils.showNotification('رسالة معلومات', 'info');
```

### مربعات الحوار (Dialogs)
```javascript
// مربع تأكيد
ActivityUtils.showConfirmDialog(
  'هل أنت متأكد؟',
  () => console.log('تم التأكيد'),
  () => console.log('تم الإلغاء')
);
```

### الطلاب العشوائيون (Random Students)
```javascript
// اختيار طالب عشوائي
const student = ActivityUtils.getRandomStudent();

// اختيار عدة طلاب
const students = ActivityUtils.getRandomStudents(3);

// خلط مصفوفة
const shuffled = ActivityUtils.shuffleArray(myArray);
```

### الحركات (Animations)
```javascript
// تحريك عنصر
ActivityUtils.animateElement(element, 'fadeIn');
ActivityUtils.animateElement(element, 'bounce');

// احتفال
ActivityUtils.celebrate();
```

### إدارة البيانات (Data Management)
```javascript
// حفظ بيانات النشاط
ActivityUtils.saveActivityData('scores', {team1: 10, team2: 15});

// تحميل بيانات النشاط
const scores = ActivityUtils.loadActivityData('scores');
```

### المؤقتات والتقدم (Timers & Progress)
```javascript
// تنسيق الوقت
const formatted = ActivityUtils.formatTime(125); // "02:05"

// تحديث شريط التقدم
ActivityUtils.updateProgress(7, 10); // 70%
```

## نظام الألوان العماني (Omani Color System)

### الألوان الأساسية (Primary Colors)
- `--omani-red`: #DC143C (الأحمر العماني)
- `--omani-green`: #228B22 (الأخضر العماني)
- `--omani-gold`: #FFD700 (الذهبي العماني)

### استخدام الألوان (Color Usage)
```css
.my-element {
  background: var(--omani-red);
  border: 2px solid var(--omani-green);
  color: var(--text-light);
}
```

## الميزات المتقدمة (Advanced Features)

### إمكانية الوصول (Accessibility)
- **اختصارات لوحة المفاتيح**: Escape للخروج، F11 للشاشة الكاملة
- **دعم قارئ الشاشة**: جميع العناصر التفاعلية مُسماة
- **وضع التباين العالي**: Alt+H
- **تكبير النص**: Ctrl++ و Ctrl+-

### التجاوب (Responsiveness)
- **تصميم الهاتف أولاً**: يبدأ من 360px
- **نقاط التوقف**: 480px، 768px، 1024px، 1400px
- **شبكات متجاوبة**: تتكيف تلقائياً مع حجم الشاشة

### الأداء (Performance)
- **تحميل مُسبق للأصوات**: تحسين الاستجابة
- **حركات محسنة**: requestAnimationFrame
- **تخزين محلي**: لحفظ الإعدادات والبيانات

## خطة التطبيق المرحلية (Implementation Plan)

### المرحلة 1: الأنشطة البسيطة
1. `random.html` - اختيار عشوائي
2. `timer.html` - المؤقت
3. `vote.html` - التصويت
4. `whois.html` - من هو

### المرحلة 2: الأنشطة المتوسطة
1. `challenges.html` - التحديات
2. `create-story.html` - إنشاء القصة
3. `gallery.html` - المعرض

### المرحلة 3: الأنشطة المعقدة
1. `quiz.html` - الاختبار (مكتمل)
2. `monopoly-oman.html` - مونوبولي عمان (جاري)
3. `Blockbusters.html` - مسابقة الحروف

## اختبار التوافق (Compatibility Testing)

بعد تطبيق النظام الموحد على كل نشاط:

1. **اختبر على أحجام شاشات مختلفة**
2. **تحقق من عمل الأصوات**
3. **اختبر إمكانية الوصول**
4. **تأكد من عمل الحركات**
5. **فحص الأخطاء في وحدة التحكم**

## الدعم والصيانة (Support & Maintenance)

- **تحديثات النظام**: في مجلد `config/`
- **إضافة ميزات جديدة**: في ملف `unified-scripts-template.js`
- **تخصيص الألوان**: في ملف `unified-styles-template.css`
- **تتبع الأخطاء**: استخدم وحدة التحكم في المتصفح

## أمثلة تطبيقية (Implementation Examples)

### مثال: تحويل نشاط بسيط
```html
<!-- قبل التحويل -->
<style>
  body { background: #f0f4f8; }
  button { background: #00796B; }
</style>

<!-- بعد التحويل -->
<link rel="stylesheet" href="../config/unified-styles-template.css">
<button class="btn btn-primary">النص</button>
```

### مثال: إضافة وظائف JavaScript
```javascript
// قبل التحويل
function showMessage(text) {
  alert(text);
}

// بعد التحويل
ActivityUtils.showNotification(text, 'success');
```

---

**ملاحظة مهمة**: هذا النظام الموحد يضمن الاتساق والجودة عبر جميع الأنشطة، مع توفير وقت التطوير وسهولة الصيانة.
