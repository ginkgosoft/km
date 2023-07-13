# การกรองข้อมูล (Filter)

1\) Mail status คือสถานะการส่งอีเมลถึงลูกค้า คลิกที่ ![](<../../.gitbook/assets/image (287).png>) เลือก Mail status อธิบายดังตาราง&#x20;

<figure><img src="../../.gitbook/assets/image (299).png" alt=""><figcaption><p>รูปที่ ‎24 Filter – Mail status</p></figcaption></figure>

ตาราง ‎: อธิบาย Mail status

| สถานะ        | คำอธิบาย                               |
| ------------ | -------------------------------------- |
| Not Send     | รายการที่ยังไม่มีการส่งอีเมลถึงผู้ซื้อ |
| Send Success | รายการที่ส่งอีเมลถึงผู้ซื้อสำเร็จ      |
| Send Failure | รายการที่ส่งอีเมลถึงผู้ซื้อไม่สำเร็จ   |
| Don’t Send   | รายการที่ไม่ต้องส่งสรรพากร             |

2\)       SMS status คือสถานะการส่ง SMS ถึงผู้ซื้อ คลิกที่ ![](<../../.gitbook/assets/image (251).png>)  อธิบายดังตาราง

<figure><img src="../../.gitbook/assets/image (275).png" alt=""><figcaption><p>Filter – SMS status</p></figcaption></figure>

ตาราง ‎: คำอธิบาย SMS status

| สถานะ        | คำอธิบาย                                  |
| ------------ | ----------------------------------------- |
| Not Send     | รายการที่ยังไม่มีการส่ง SMS ถึงผู้ซื้อ    |
| Send Success | รายการที่มีการส่ง SMS ถึงผู้ซื้อสำเร็จ    |
| Send Failed  | รายการที่มีการส่ง SMS ถึงผู้ซื้อไม่สำเร็จ |
| Don’t Send   | รายการที่กำหนดไม่ส่งถึงผู้ซื้อ            |

3\) zDOX status คือสถานะการอัปโหลดไฟล์ขึ้น zDOX ของผู้ซื้อ ![](<../../.gitbook/assets/image (240).png>) อธิบายดังตาราง

<figure><img src="../../.gitbook/assets/image (203).png" alt=""><figcaption><p>รูปที่ ‎26 Filter - zDOX status</p></figcaption></figure>

ตาราง ‎: อธิบาย SMS Status

| สถานะ        | คำอธิบาย                                        |
| ------------ | ----------------------------------------------- |
| Not Send     | รายการที่ยังไม่มีการอัปโหลดขึ้น zDOX ของผู้ซื้อ |
| Send Success | รายการที่อัปโหลดขึ้น zDOX ของผู้ซื้อสำเร็จ      |
| Send Failed  | รายการที่อัปโหลดขึ้น zDOX ของผู้ซื้อไม่สำเร็จ   |

4\) Key-In Invoice คือการกรองข้อมูลโดยแยกประเภทรายการข้อมูลอิเล็กทรอนิกส์ที่นำมา Generate ที่ระบบ getInvoice คลิกที่  ![](<../../.gitbook/assets/image (249).png>)  อธิบายดังError! Reference source not found. อธิบาย Key-In Invoice

| สถานะ       | คำอธิบาย                                                                                                                                                  |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Non Key-In  | รายการข้อมูลอิเล็กทรอนิกส์ประเภท .xml, .csv, .xlsx, .txt ที่นำเข้าโดยผ่านช่องทาง zDOX, REST API, SFTP, Email ![](<../../.gitbook/assets/image (259).png>) |
| Key-In Only | รายการข้อมูลที่ทำการสร้างที่เมนู Create An Invoice เท่านั้น ![](<../../.gitbook/assets/image (239).png>)                                                  |

5\)  Job type คือการกรองข้อมูลโดยแยกตามชนิดงาน ได้แก่ Sign Document ซึ่งแสดงเอกสารที่ถูกลงนามแล้ว วิธีการเลือกการกรองนี้ รายละเอียดตามภาพด้านล่าง

<figure><img src="../../.gitbook/assets/image (209).png" alt=""><figcaption><p>Job type - Sign Document</p></figcaption></figure>

6\)  Dropdown list ตัวเลือกสำหรับกำหนดค้นหาข้อมูล ได้แก่ Document No., Buyer Name, Email, Telephone และ Source

<figure><img src="../../.gitbook/assets/image (223).png" alt=""><figcaption><p>Send to Buyer – ตัวเลือกสำหรับกำหนดค้นหาข้อมูล</p></figcaption></figure>

7\) กรองข้อมูลตามสาขา หรือแผนก หากมีบริษัทมีหลายสาขา สามารถกรองข้อมูลตามสาขา หรือ แผนกได้ โดยเลือกที่สัญลักษณ์ <img src="../../.gitbook/assets/image (10) (2).png" alt="" data-size="line"> จากนั้นเลือกกรอง Department จากนั้นเลือกแผนก หรือ สาขา ที่ต้องการ

<mark style="color:purple;">(กรณีไม่มีแผนก หรือ สาขา Filter จะไม่ปรากฎหัวข้อ Department)</mark>

<figure><img src="../../.gitbook/assets/image (6) (2).png" alt=""><figcaption><p>Send to buyer - วิธีการเลือกตัวกรอง</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Send to buyer - เลือก Department ใน Filter</p></figcaption></figure>
