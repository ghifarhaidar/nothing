&#x202b;

# مشروع e-commerce recommendation system

## وصف المشروع

يهدف هذا المشروع إلى تطوير Extension لنظام إدارة محتوى التسوق الالكتروني OpenCart، يعتمد على سلوك المستخدم لاستنتاج وعرض اقتراحات المنتجات المناسبة.

يشمل المشروع المكونات الأساسية التالية:

- منصة [OpenCart](https://www.opencart.com/).
- مشروع منفصل مخصص لإنشاء نموجذ sli_rec وتدريبه.

## هيكلية المشروع

تم الحصول على الرماز البرحمي لمنصة OpenCart من الموقع الرسي للمنصة.
المجلد الرئيسي له هو مجلد upload.

المشروع المنفصل الذي يتم به تدريب النموذج موجود في المجلد الرئيسي ml.

### تفاصيل الملفات والمجلدات في قسم إنشاء النموذج

| الملف/المجلد         | الوصف                                                  |
| -------------------- | ------------------------------------------------------ |
| `creating_model.py`  | الملف الرئيسي لإنشاء النموذج وتدريبه.                  |
| `data.py`            | الملف الذي تم من خلاله إنشاء بيانات التدريب.           |
| `SeqModelWrapper.py` | الملف الذي يحوي تغليف النموذج المختار.                 |
| `util.py`            | ملف مساعد يحوي توابع معالجة البيانات.                  |
| `config/`            | يحتوي على ملفات إعدادات النماذج مثل المعاملات الفائقة. |
| `resources/`         | يحوي على بيانات التدريب.                               |

## بيانات التدريب

بيانات التدريب تتكون من ملفين نصيين json

الملف الأول يحوي معلومات عامة عن المنتجات التي يوفرها المتجر الالكتروني ، مثال عنها :

```
{"ItemID": '1005', "Name": "Gaming Console", "Category": "Electronics", "CategoryID": '2001', "Subcategory": "Gaming", "SubcategoryID": '3005'}
{"ItemID": '1006', "Name": "DSLR Camera", "Category": "Electronics", "CategoryID": '2001', "Subcategory": "Cameras", "SubcategoryID": '3006'}
{"ItemID": '1007', "Name": "Bluetooth Speaker", "Category": "Electronics", "CategoryID": '2001', "Subcategory": "Audio", "SubcategoryID": '3004'}
{"ItemID": '1008', "Name": "Tablet", "Category": "Electronics", "CategoryID": '2001', "Subcategory": "Mobile Devices", "SubcategoryID": '3007'}
```

الملف الثاني يحوي بيانات تفاعل المستخدمين مع المنتجات في الموقع، مثال عنها:

```
{"UserID":"user_1","ItemID":1200,"ItemName":"Diecast Car Set","Category":"Toys and Games","CategoryID":2010,"InteractionType":"view","Timestamp":"2020-06-04 10:18:14"}
{"UserID":"user_1","ItemID":1195,"ItemName":"Toy Helicopter","Category":"Toys and Games","CategoryID":2010,"InteractionType":"view","Timestamp":"2020-06-02 07:47:14"}
{"UserID":"user_1","ItemID":1195,"ItemName":"Toy Helicopter","Category":"Toys and Games","CategoryID":2010,"InteractionType":"add to cart","Timestamp":"2020-06-02 08:00:14"}
{"UserID":"user_1","ItemID":1195,"ItemName":"Toy Helicopter","Category":"Toys and Games","CategoryID":2010,"InteractionType":"review 2","Timestamp":"2020-06-02 08:15:14"}
```

## النموذج المدرب

تم الحصول على النموذج المدرب من مكتبة [Microsoft Recommenders ](https://github.com/recommenders-team/recommenders).

وتم استخدان نموذج [SLi_Rec](https://github.com/recommenders-team/recommenders/blob/main/examples/00_quick_start/sequential_recsys_amazondataset.ipynb).
