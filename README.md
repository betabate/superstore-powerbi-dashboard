# 📈 Retail Sales & Profitability Analytics Dashboard (Superstore)

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Power Query](https://img.shields.io/badge/Power_Query_ETL-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Business Intelligence](https://img.shields.io/badge/Business_Analytics-FF6F00?style=for-the-badge)

## 📌 Project Overview
โปรเจกต์การวิเคราะห์ผลการดำเนินงานด้านยอดขายและกำไรในธุรกิจค้าปลีก (Retail Superstore) ตั้งแต่ปี 2014–2017 ด้วย **Microsoft Power BI** เพื่อช่วยผู้บริหารติดตามดัชนีชี้วัดหลัก (KPIs), วิเคราะห์แนวโน้มยอดขายตามฤดูกาล (Seasonality), และค้นหาหมวดหมู่สินค้าที่สร้างผลขาดทุนสุทธิเพื่อปรับปรุงกลยุทธ์การตั้งราคาและโปรโมชัน

---

## 🖥️ Dashboard Preview

![Superstore Dashboard Overview](assets/superstore_dashboard.png)

<!-- หากมีไฟล์ GIF ตอนกด Slicer เลือกปี/หมวดหมู่ ให้ลบเครื่องหมายคอมเมนต์ด้านล่างออก -->
<!-- ![Interactive Demo](assets/superstore_demo.gif) -->

---

## 🛠️ Data Preparation & Technical Implementation

1. **Data Cleaning & Transformation (Power Query):**
   * ตรวจสอบและจัดรูปแบบประเภทข้อมูล (Data Types) ด้านการเงินและวันที่ (`Order Date`, `Ship Date`)
   * สกัดมิติเวลา (`Order Year`, `Order Month`) เพื่อรองรับการวิเคราะห์ข้อมูลอนุกรมเวลา (Time Series Analysis)
2. **DAX Measures & KPI Formulation:**
   สร้างตัวชี้วัดแบบไดนามิกด้วยภาษา **DAX** ที่คำนวณเปลี่ยนตามบริบทการกรองของผู้ใช้ (Filter Context):
   ```dax
   // ยอดขายรวมทั้งหมด
   Total sale = SUM('Sample - Superstore'[Sales])

   // กำไรสุทธิรวม
   Total profit = SUM('Sample - Superstore'[Profit])

   // อัตรากำไรขั้นต้น (%)
   Profit Margin % = DIVIDE([Total profit], [Total sale], 0)

   // จำนวนคำสั่งซื้อทั้งหมด (Unique Orders)
   Total Order = DISTINCTCOUNT('Sample - Superstore'[Order ID])
   ```
3. **Dashboard Design & Storytelling:**
   * **Executive KPI Cards:** สรุปภาพรวม 4 ตัวชี้วัดหลัก (`Total sale`, `Total profit`, `Profit Margin %`, `Total Order`) ไว้ด้านบนสุดตามหลักการกวาดสายตา (Z-Pattern Layout)
   * **Monthly Trend Analysis:** ใช้กราฟเส้นเปรียบเทียบการเติบโตของยอดขายและกำไรรายเดือน (เดือน 1–12)
   * **Category & Sub-Category Breakdown:** วิเคราะห์สัดส่วนรายได้ใน 3 หมวดหมู่หลัก และเจาะลึกเปรียบเทียบยอดขายเทียบกับกำไรใน 17 หมวดหมู่ย่อย

---

## 💡 Key Business Insights (ข้อมูลเชิงลึกที่ค้นพบ)

* **Overall Financial Performance:** ธุรกิจมียอดขายรวมทั้งสิ้น **$2.30M** สร้างกำไรสุทธิ **$286.40K** คิดเป็นอัตรากำไรขั้นต้น (**Profit Margin**) เฉลี่ยที่ **12.47%** จากคำสั่งซื้อทั้งหมดประมาณ **5,000 คำสั่งซื้อ**
* **Balanced Revenue Distribution:** ยอดขายกระจายตัวอยู่ใน 3 หมวดหมู่หลักอย่างใกล้เคียงกัน ได้แก่ **Technology** (`$836.15K` / `36.4%`), **Furniture** (`$742.00K` / `32.3%`), และ **Office Supplies** (`$719.05K` / `31.3%`)
* **Seasonal Sales Peaks (Q4 Surge):** จากกราฟแนวโน้มรายเดือน ยอดขายจะเติบโตขึ้นอย่างก้าวกระโดดในช่วง **เดือนกันยายน (เดือน 9)** และพุ่งขึ้นสูงสุดในช่วงไตรมาสสุดท้ายของปี (**พฤศจิกายน–ธันวาคม**) ซึ่งเป็นช่วงเทศกาลจับจ่ายใช้สอย
* **Unprofitable Sub-Categories (จุดรั่วไหลของกำไร):** 
  * แม้สินค้ากลุ่ม **`Phones`** และ **`Chairs`** จะทำยอดขายได้สูงสุดเป็นอันดับ 1 และ 2 ของบริษัท แต่เมื่อวิเคราะห์กำไรรายหมวดหมู่ย่อยพบว่ากลุ่ม **`Tables` (โต๊ะ)** และ **`Bookcases` (ตู้หนังสือ)** มียอดขายสูงแต่กลับ **ขาดทุนสุทธิ (Negative Profit)**
  * **ข้อเสนอแนะเชิงธุรกิจ (Actionable Recommendation):** ฝ่ายการตลาดและฝ่ายขายควรทบทวนเพดานการให้ส่วนลด (Discount Rate) และต้นทุนค่าขนส่งของสินค้ากลุ่ม `Tables` และ `Bookcases` ทันที เพื่อเปลี่ยนยอดขายที่สูงให้กลับมาเป็นกำไร

---

## 📂 Repository Structure
* `superstore_report.pbix` - ไฟล์ต้นฉบับ Power BI Desktop
* `superstore_report.pdf` - ไฟล์รายงาน Dashboard รูปแบบ PDF
* `Sample - Superstore.csv` - ชุดข้อมูลต้นฉบับที่ใช้ในการวิเคราะห์
