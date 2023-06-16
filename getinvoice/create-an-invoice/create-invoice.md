# Create Invoice

1. ผู้ใช้งานคลิกเมนู CREATE AN INVOICE ระบบแสดงหน้าจอ Manage Invoices กดที่ปุ่ม Create Invoice ระบบจะแสดงหน้าจอสร้างใบกำกับภาษีอิเล็กทรอนิกส์หรือใบรับอิเล็กทรอนิกส์

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption><p>หน้าจอ Manage Invoices</p></figcaption></figure>

2. เลือกประเภทเอกสารและกรอกข้อมูลให้ครบถ้วน โดยช่องข้อมูลที่จำเป็นต้องกรอกจะแสดงเป็นเส้นสีส้ม

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>หน้าจอ Create Invoice – ข้อมูล Require field</p></figcaption></figure>

3. กำหนดแสดง Tax หรือ Allowance ของ Line Item โดยคลิกที่ช่อง checkbox ของ Inline Tax หรือ Inline Allowance

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption><p>หน้าจอ Create Invoice – กำหนดเลือก Inline Tax หรือ Inline Allowance</p></figcaption></figure>

4. กำหนดประเภทของ Tax เลือก TAX Exclusive หรือ TAX Inclusive โดยมี Default เป็น TAX Exclusive ซึ่งสามารถกำหนดได้ที่ Default Setting

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>หน้าจอ Create Invoice – Price TAX</p></figcaption></figure>

5. Allowance

5.1 กำหนดวิธีการคำนวณ Allowance โดย

**Cumulative Allowance** เป็นการคิดคำนวณเพิ่ม/ลด Allowance แบบสะสม

**Allowance from Original** เป็นการคิดคำนวณเพิ่ม/ลด Allowance แบบโดยอ้างอิงราคาจาก Unit Price

เลือกในแถบตามภาพด้านล่าง&#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>หน้าจอกำหนดการคำนวณ Allowance</p></figcaption></figure>

5.2 กำหนดประเภทของ Allowance โดยกดที่ Add Allowance จะปรากฎ Pop-up ขึ้นมา ขั้นแรกเลือก Charge หรือ Discount โดยกดเลือกที่ circle bottom หน้าข้อความ (หมายเลข 1) ขั้นที่ 2 เลือกชนิดของค่าธรรมเนียม/ค่าส่วนลด โดยกดที่ปุ่มสามเหลี่ยมที่มุมด้านขวา (หมายเลข 2) ขั้นที่ 3 เลือกรูปแบบของ Charge/Discount ว่าให้เป็นรูปแบบของ Amount (จำนวนเงิน) หรือ Percent (เปอร์เซ็นต์) (หมายเลข 3) และขั้นที่ 4 กรอกจำนวนเงินหรือเปอร์เซ็นต์ ของ Charge/Discount (หมายเลข 4) ซึ่งหัวข้อ Add Allowance ไม่ใช่หัวข้อบังคับ

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>หน้าจอ Allowance </p></figcaption></figure>

หลังจากนั้น กดที่่ปุ่ม Add ตามภาพด้านล่าง

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>กด Add ของหน้าจอ Allowance </p></figcaption></figure>

ตาราง : Allowance&#x20;

| สัญลักษณ์                                   | คำอธิบาย                                        |
| ------------------------------------------- | ----------------------------------------------- |
| ![](<../../.gitbook/assets/image (13).png>) | ค่าธรรมเนียม/ส่วนลด ที่มีมูลค่าเป็นจำนวนเงิน    |
| ![](<../../.gitbook/assets/image (8).png>)  | ค่าธรรมเนียม/ส่วนลด ที่มีมูลค่าเป็นเปอร์เซ็นต์  |

6. ข้อมูล Customer (Buyer) สามารถกรอกคำค้นและเลือกจากข้อมูลที่มีอยู่ใน Settings Buyers ดูรายละเอียดเพิ่มเติมได้ในหัวข้อ [Setting](settings.md) หรือคลิกไอคอน ![](<../../.gitbook/assets/image (64).png>) เพื่อทำการเพิ่มข้อมูล Buyers ใหม่ได้

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption><p>หน้าจอ Create Invoice - ข้อมูล Buyer</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption><p>หน้าจอ Create Invoice - หน้าจอเพิ่มข้อมูล Buyer</p></figcaption></figure>

7. รายการ Item สามารถกรอกคำค้นและเลือกจากข้อมูลที่มีอยู่ใน Settings Items ดูรายละเอียดเพิ่มเติมได้ในหัวข้อ [Setting](settings.md) หรือกรอกข้อมูลให้ครบถ้วน โดยรายการที่เพิ่มใหม่เมื่อบันทึกสร้างเรียบร้อยแล้ว ระบบจะบันทึกข้อมูล Item จัดเก็บไว้ในระบบ Settings: Items ให้อัตโนมัติ ไว้สำหรับใช้สร้างรายการในครั้งถัดไป

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption><p>Create Invoice – ค้นหาหรือกรอกข้อมูล Items</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption><p>Create Invoice – เพิ่มข้อมูล Items</p></figcaption></figure>

8. ประเภท Debit Note และ Credit Note สามารถกำหนดให้กรอก Old Price และ New Price ได้โดยกำหนดตั้งค่าใน Default Setting ให้เรียบร้อยก่อนสร้าง

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Create Invoice – กรอกข้อมูล Old Price และ New Price</p></figcaption></figure>

9. หลังจากกรอกข้อมูลครบถ้วนแล้ว กดปุ่ม Save

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption><p>Create Invoice – Save บันทึกสร้าง</p></figcaption></figure>

10. เมื่อบันทึกสร้างเรียบร้อยแล้ว ผู้สร้างสามารถแก้ไข คัดลอก ลบ หรือ Generate PDF เอกสารที่สร้างได้ โดยที่เอกสารนั้นยังต้องไม่มีการ Send to Buyer กรณีผู้ใช้ต้องการ Export ไฟล์ XML สามารถกดเข้าไปใน Edit

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption><p>Create Invoice – Edit</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption><p>Create Invoice – Export XML</p></figcaption></figure>

11. กดปุ่ม Generate PDF ระบบแสดงหน้าจอ Generate PDF เลือก Template และกำหนด Output ที่ต้องการ กดปุ่ม Generate

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption><p>Create Invoice – Generate PDF</p></figcaption></figure>

12. เมื่อ Generate สำเร็จระบบจะแสดง PDF ตรงตามประเภทเอกสารที่ผู้ใช้งานกรอกถูกต้อง

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Create Invoice – Generated PDF</p></figcaption></figure>

13. หลังจากระบบทำการสร้างใบกำกับภาษีอิเล็กทรอนิกส์หรือใบรับอิเล็กทรอนิกส์เรียบร้อย ผู้ใช้งานระบบสามารถตรวจสอบไฟล์ PDF ก่อนจัดส่งให้ลูกค้าได้ที่เมนู REVIEW INVOICE และเมนู SEND TO BUYER รวมถึงสามารถตรวจสอบไฟล์ XML ก่อนจัดส่งให้กรมสรรพากรได้ที่เมนู SEND TO RD

<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>Create Invoice – Review Invoice</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption><p>Create Invoice – Send To Buyer</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption><p>Create Invoice – Send To RD</p></figcaption></figure>

14. กรณีผู้ใช้งานระบบต้องการแก้ไขข้อมูลที่เคยบันทึกไว้ สามารถทำได้โดยเลือกรายการใบกำกับภาษีอิเล็กทรอนิกส์หรือใบรับอิเล็กทรอนิกส์ที่ต้องการแก้ไข ![](<../../.gitbook/assets/image (87).png>) และกด Edit โดยเอกสารที่สามารถแก้ไขได้แต่จะต้องไม่มีการ Send to Buyer มาก่อน หน้า Edit Invoice ให้ผู้ใช้งานทำการแก้ไขข้อมูลและหากผู้ใช้งานระบบต้องการลบ Item ให้กดที่สัญลักษณ์รูปถังขยะ ![](<../../.gitbook/assets/image (433).png>) ระบบจะทำการลบรายการ Item ที่เลือกออกจากระบบ

<figure><img src="../../.gitbook/assets/image (451).png" alt=""><figcaption><p>หน้าจอ Manage Invoices – Edit Invoice</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (442).png" alt=""><figcaption><p>หน้าจอ Invoice Details - แก้ไข Line Item</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (526).png" alt=""><figcaption><p>หน้าจอ Invoice Details - ลบ Line Item</p></figcaption></figure>

15. กรณีผู้ใช้งานระบบต้องการลบรายการใบกำกับภาษีอิเล็กทรอนิกส์หรือใบรับอิเล็กทรอนิกส์ที่สร้างไว้ ให้กดที่ปุ่ม Delete ระบบแสดงข้อความยืนยันการลบ หากไม่ต้องการยืนยันการลบให้กดปุ่ม Cancel หากต้องการยืนยันการลบให้กดปุ่ม Delete ระบบจะทำการลบรายการใบกำกับภาษีอิเล็กทรอนิกส์หรือใบรับอิเล็กทรอนิกส์นั้น

<figure><img src="../../.gitbook/assets/image (483).png" alt=""><figcaption><p>หน้าจอ Invoice Details - ลบรายการ Invoice</p></figcaption></figure>

16. กรณีผู้ใช้ระบบต้องการกด Copy Invoice ระบบจะทำการคัดลอกรายละเอียดของเอกสารนั้นๆ ให้เหมือนกันทั้งหมดโดยจะอยู่ในหน้าที่สามารถแก้ไขเอกสาร หากไม่มีการตั้งค่า Running Number และไม่ได้แก้ไขเลขที่เอกสารนั้น ๆ จะซ้ำกันเมื่อกด Save จะมีการแจ้งเตือนเอกสารเป็น Duplicate โดยเอกสารใบเก่าจะถูกแก้ไขสถานะเป็น Duplicate แทน

<figure><img src="../../.gitbook/assets/image (482).png" alt=""><figcaption><p>หน้าจอ Manage Invoices – Edit Invoice</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (438).png" alt=""><figcaption><p>หน้าจอ Manage Invoices – Duplicate Invoice</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (516).png" alt=""><figcaption><p>หน้าจอ Manage Invoices – หน้า Manage Invoice สถานะ Duplicate</p></figcaption></figure>
