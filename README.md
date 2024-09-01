&#x202b;

# مشروع e-commerce recommendation system

## وصف المشروع

يهدف هذا المشروع إلى تطوير Extension لنظام إدارة محتوى التسوق الالكتروني OpenCart، يعتمد على سلوك المستخدم لاستنتاج وعرض اقتراحات المنتجات المناسبة.

يشمل المشروع المكونات الأساسية التالية:

- منصة OpenCart.
- مشروع منفصل مخصص لإنشاء نموجذ sli_rec وتدريبه.

## هيكلية المشروع

تم الحصول على الرماز البرحمي لمنصة OpenCart من الموقع الرسي للمنصة.
المجلد الرئيسي له هو مجلد upload.

الشمروع المنفصل الذي يتم به تدريب النموذج موجود في المجلد الرئيسي ml.

### تفاصيل الملفات والمجلدات

| الملف/المجلد | الوصف                                                                                           |
| ----------------------- | ---------------------------------------------------------------------------------------------------- |
| `creating_model.py`   | الملف الرئيسي لإنشاء النموذج وتدريبه.                                |
| `data.py`             | الملف الذي تم من خلاله إنشاء بيانات التدريب.                     |
| `SeqModelWrapper.py`  | الملف الذي يحوي تغليف النموذج المختار.                               |
| `util.py`             | ملف مساعد يحوي توابع معالجة البيانات.                                 |
| `config/`             | يحتوي على ملفات إعدادات النماذج مثل المعاملات الفائقة. |
| `resources/`          | يحوي على بيانات التدريب.                                                         |

## بيانات التدئيب

بيانات التدريب تتكون من ملفين نصيين json
الملف الأول يحوي معلومات عامة عن المنتجات التي يوفرها المتجر الالكتروني ، مثال عنها :

## الإعداد والتشغيل

1. **تثبيت المتطلبات** :
   تأكد من تثبيت جميع المكتبات اللازمة. يمكن تثبيتها باستخدام:

<pre><div class="dark bg-gray-950 contain-inline-size rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>bash</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-bash">pip install -r requirements.txt
   </code></div></div></pre>

1. **تشغيل المشروع** :
   لتشغيل المشروع، استخدم:

<pre><div class="dark bg-gray-950 contain-inline-size rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>bash</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-bash">python main.py
   </code></div></div></pre>

## بيانات التدريب والنماذج المدربة مسبقًا

- **البيانات** : البيانات المستخدمة في التدريب متاحة في مجلد `data/`. يمكن تحميل البيانات الخام من [رابط البيانات](#) إذا لم تكن موجودة في المجلد.
- **النماذج المدربة مسبقًا** : النماذج المدربة مسبقًا موجودة في `data/pre-trained-models/`، ويمكن تحميلها من [رابط النموذج](#) إذا لم تكن موجودة.

## ملفات الإخراج والنتائج

- **النتائج** : سيتم حفظ نتائج النماذج، مثل التقييمات وتسجيل الأداء، في مجلد `results/`.
- **الملفات المؤقتة** : سيتم تخزين أي ملفات مؤقتة أو سجلات في مجلد `logs/`.

## ملاحظات إضافية

- **الخدمات الخارجية** : يستخدم المشروع خدمات خارجية مثل [Cloud API](#) أو خوادم داخلية مثل [GPU Server](#) لتسريع عمليات المعالجة.
- **إعدادات المشروع** : يتم تحديد جميع إعدادات المشروع مثل `Thresholds` و `Hyperparameters` في مجلد `config/`.

## المراجع والمصادر

- **مستودع المشروع** : [رابط المستودع على GitHub](#)
- **مستندات إضافية** : تحتوي مستندات المشروع في مجلد `docs/` على مزيد من التفاصيل حول كيفية عمل المشروع.

