# Recipe AI System 🍲📸

מערכת לזיהוי מתכונים מתוך תמונה, קבלת מתכונים דומים, וסינון חכם לפי העדפות המשתמש.

---

## 🔧 טכנולוגיות בשימוש

- **Backend**: Python + Flask
- **Frontend**: Angular
- **Model**: Vision Transformer (ViT) + Cosine Similarity
- **אחסון זמני**: Excel (לפי `user_id`)
- **קבצים חשובים**:
  - `connect_everyone.py`: זיהוי תמונה ואיתור מתכונים דומים
  - `good_qution.py`: סינון לפי תשובות והחזרת שאלה או תוצאה
  - `Recipe_details.py`: זיהוי מתכון מנצח
  - `temp_recipes/`: תיקייה למתכונים זמניים לכל משתמש

---

## 🚀 תהליך העבודה

1. **משתמש מעלה תמונה מהטלפון / מצלמה באפליקציית Angular**.
2. **קריאה לשרת Flask** (`/get_similar_images`) עם `image_path` + `user_id`.
3. השרת:
   - מחשב דמיון בין תמונות ומייצר קובץ Excel של מתכונים דומים.
   - בודק אילו שאלות יש לשאול את המשתמש.
   - מחזיר JSON: או שאלה, או תוצאה.
4. אם יש שאלה, המשתמש עונה → Angular שולחת ל-`/submit_answer`.
5. חוזר עד שיש מתכון מנצח או פחות מ-3 מתכונים.

---

## 📁 מבנה התיקיות

```bash
project-root/
├── app.py                   # שרת Flask הראשי
├── good_qution.py           # סינון לפי שאלות
├── connect_everyone.py      # הפקת embedding והשוואת תמונות
├── Recipe_details.py        # בחירת מתכון סופי
├── temp_recipes/            # קבצים זמניים לפי user_id
├── similar_recipes.xlsx     # תוצאה זמנית של זיהוי
└── frontend/                # פרויקט Angular (נפרד)



🛠️ התקנה והרצה
 Backend (Flask):
# 1. יצירת סביבת פיתוח
python -m venv venv
source venv/bin/activate  # ב-Windows: venv\Scripts\activate

# 2. התקנת תלויות
pip install -r requirements.txt

# 3. הרצה
python app.py


flask
flask-cors
pandas
openpyxl
transformers
torch
scikit-learn

