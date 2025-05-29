markdown# ระบบแจ้งซ่อมไฟฟ้า - อบต.ข่าใหญ่

ฟอร์มสำหรับกรอกข้อมูลผู้แจ้งซ่อมไฟฟ้า

## การใช้งาน
- เปิดฟอร์มผ่าน LINE Bot
- กรอกข้อมูลส่วนตัว
- ระบบจะบันทึกข้อมูลใน Google Sheets

## เทคโนโลยี
- HTML5, CSS3, JavaScript
- Google Apps Script
- LINE Messaging API
.gitignore:
# System files
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/

# Temp files
*.tmp
*.log
⚙️ ขั้นตอนสำคัญหลัง Deploy
1. อัพเดต GAS_URL ใน HTML:
javascript// แก้ไขใน index.html
GAS_URL: 'https://script.google.com/macros/s/YOUR_ACTUAL_SCRIPT_ID/exec'
2. อัพเดต CORS ใน Google Apps Script:
javascript// เพิ่ม Render URL ใน ALLOWED_ORIGINS
3. ทดสอบการทำงาน:
https://your-render-app.onrender.com?userId=TEST123
🎯 ข้อดีของ Render

✅ ฟรี: Static site deploy ฟรี
✅ Auto Deploy: Push โค้ดใหม่จะ deploy อัตโนมัติ
✅ HTTPS: มี SSL Certificate ให้อัตโนมัติ
✅ Custom Domain: ใช้ domain ของตัวเองได้
✅ CDN: เร็วทั่วโลก

📱 วิธีใช้งานจริง
ใน LINE Bot (GSA) จะเรียกใช้:
javascriptconst formMessage = {
  type: "template",
  altText: "กรอกข้อมูลผู้แจ้ง",
  template: {
    type: "buttons",
    text: formMsg,
    actions: [{
      type: "uri",
      label: "📝 เปิดฟอร์มกรอกข้อมูล",
      uri: `https://your-render-app.onrender.com?userId=${encodeURIComponent(userId)}`
    }]
  }
};
