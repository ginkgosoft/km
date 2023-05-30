# การกรองข้อมูล (Filter)

Status คือสถานะของ Generate, Email, SMS, zDOX และ RD ที่ส่งไม่สำเร็จ คลิกที่ อธิบายดังตาราง

ตาราง ‎: อธิบาย Status

| สถานะ              | คำอธิบาย                                                                                             |
| ------------------ | ---------------------------------------------------------------------------------------------------- |
| Generate Failure   | กรองข้อมูลรายการที่ Generate ไม่สำเร็จ ![](<../../.gitbook/assets/image (222).png>)                  |
| Send Email Failure | กรองข้อมูลรายการที่ส่งอีเมลถึงผู้ซื้อไม่สำเร็จ ![](<../../.gitbook/assets/image (294).png>)          |
| Send SMS Failure   | กรองข้อมูลรายการที่ส่ง SMS ถึงผู้ซื้อไม่สำเร็จ ![](<../../.gitbook/assets/image (216).png>)          |
| Send zDOX Failure  | กรองข้อมูลรายการที่อัปโหลดขึ้น zDOX ของผู้ซื้อไม่สำเร็จ ![](<../../.gitbook/assets/image (202).png>) |
| Send RD Failure    | กรองข้อมูลรายการที่ส่งสรรพากรไม่สำเร็จ ![](<../../.gitbook/assets/image (257).png>)                  |

**2) Key-In Invoice คือการกรองข้อมูลโดยแยกประเภทรายการข้อมูลอิเล็กทรอนิกส์ที่นำมา Generate ที่ระบบ getInvoice คลิกที่**  ![](<../../.gitbook/assets/image (271).png>) **อธิบายดังตาราง**

ตาราง : อธิบาย Key-In Invoice

| สถานะ       | คำอธิบาย                                                                                                                                                  |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Non Key-In  | รายการข้อมูลอิเล็กทรอนิกส์ประเภท .xml, .csv, .xlsx, .txt ที่นำเข้าโดยผ่านช่องทาง zDOX, REST API, SFTP, Email ![](<../../.gitbook/assets/image (237).png>) |
| Key-In Only | รายการข้อมูลที่ทำการสร้างที่เมนู Create An Invoice เท่านั้น ![](<../../.gitbook/assets/image (242).png>)                                                  |

3\) Dropdown list ตัวเลือกสำหรับกำหนดค้นหาข้อมูล ได้แก่ Document No., Buyer Name, Email, Telephone, Source และ Job ID, Item ID

<figure><img src="../../.gitbook/assets/image (418).png" alt=""><figcaption><p>Transaction – ตัวเลือกสำหรับกำหนดค้นหาข้อมูล</p></figcaption></figure>
