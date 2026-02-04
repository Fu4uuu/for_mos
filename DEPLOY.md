# Deploy หน้า HTML ขึ้น GitHub (GitHub Pages)

## ขั้นตอนที่ 1: สร้าง Repository บน GitHub

1. ไปที่ [github.com/new](https://github.com/new)
2. ตั้งชื่อ repo เช่น `my-html-page` หรือ `test-page`
3. เลือก **Public**
4. **อย่าติ๊ก** "Add a README" (เรามีไฟล์อยู่แล้ว)
5. กด **Create repository**

---

## ขั้นตอนที่ 2: Push โค้ดขึ้น GitHub

เปิด Terminal/PowerShell ในโฟลเดอร์ `d:\test` แล้วรันคำสั่งด้านล่าง (แทน `YOUR_USERNAME` และ `YOUR_REPO` ด้วยชื่อจริงของคุณ):

```powershell
# ถ้ามี index.lock ให้ลบก่อน (ถ้า git บอกว่ามี process อื่นรันอยู่)
Remove-Item -Force .git\index.lock -ErrorAction SilentlyContinue

# เพิ่มไฟล์และ commit
git add .
git commit -m "Initial commit: HTML page"

# เชื่อมกับ repo บน GitHub (เปลี่ยน YOUR_USERNAME และ YOUR_REPO)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git

# ส่งโค้ดขึ้น GitHub (สาขา main)
git branch -M main
git push -u origin main
```

ถ้า GitHub ขอ username/password ให้ใช้ **Personal Access Token** แทนรหัสผ่าน (Settings → Developer settings → Personal access tokens).

---

## ขั้นตอนที่ 3: เปิด GitHub Pages (Deploy หน้าเว็บ)

1. เข้า repo บน GitHub ที่สร้างไว้
2. ไปที่ **Settings** → ด้านซ้ายเลือก **Pages**
3. ใต้ **Source** เลือก **Deploy from a branch**
4. ใต้ **Branch** เลือก **main** และโฟลเดอร์ **/ (root)**
5. กด **Save**

รอ 1–2 นาที หน้าเว็บจะอยู่ที่:

**https://YOUR_USERNAME.github.io/YOUR_REPO/**

---

## สรุป URL

- Repo: `https://github.com/YOUR_USERNAME/YOUR_REPO`
- หน้าเว็บ (หลังเปิด Pages): `https://YOUR_USERNAME.github.io/YOUR_REPO/`

---

## ถ้าไฟล์บน GitHub อัปเดตแล้ว แต่หน้าเพจยังเป็นเวอร์ชันเก่า

1. **เช็กการตั้งค่า Pages**
   - เข้า repo → **Settings** → **Pages**
   - ต้องเป็น **Source: Deploy from a branch**
   - **Branch:** เลือก **main** (ไม่ใช่ gh-pages)
   - **Folder:** เลือก **/ (root)** (ไม่ใช่ /docs)
   - กด **Save** อีกครั้ง (บังคับให้ deploy ใหม่)

2. **เช็กว่าโหลดเวอร์ชันล่าสุด**
   - เปิด https://fu4uuu.github.io/for_my_friend/
   - กด **Ctrl+U** (View Page Source)
   - หาบรรทัด `<!-- v=20250203-2 ...` ถ้าเห็นเลขนี้ = หน้าเพจอัปเดตแล้ว  
   - ถ้าไม่เห็น = ยัง cache อยู่ → ลอง **Ctrl+Shift+R** หรือเปิดใน Incognito

3. **เปิดด้วย URL เติม query (หลีก cache)**
   - ลองเปิด: `https://fu4uuu.github.io/for_my_friend/?nocache=1`
