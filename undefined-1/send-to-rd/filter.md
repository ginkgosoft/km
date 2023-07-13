# การกรองข้อมูล (Filter)

1\)       RD Status คือสถานะการส่งข้อมูลให้สรรพากร คลิกที่ ![](<../../.gitbook/assets/image (293).png>)  อธิบายดังตาราง

ตาราง ‎: อธิบาย RD Status

| สถานะ        | คำอธิบาย                                                                               |
| ------------ | -------------------------------------------------------------------------------------- |
| Not Send     | กรองข้อมูลรายการที่ยังไม่ได้ส่งสรรพากร ![](<../../.gitbook/assets/image (292).png>)    |
| Send Success | กรองข้อมูลรายการที่ส่งสรรพากรสำเร็จ ![](<../../.gitbook/assets/image (220).png>)       |
| No Response  | กรองข้อมูลรายการที่รอการตอบกลับจากสรรพากร ![](<../../.gitbook/assets/image (232).png>) |
| Send Failed  | กรองข้อมูลรายการที่ส่งสรรพากรไม่สำเร็จ ![](<../../.gitbook/assets/image (201).png>)    |

| สถานะ     | คำอธิบาย                                                                              |
| --------- | ------------------------------------------------------------------------------------- |
| Cancelled | กรองข้อมูลรายการที่ผู้ใช้งานทำการ Reject ![](<../../.gitbook/assets/image (221).png>) |

2\)       Key-In Invoice คือการกรองข้อมูลโดยแยกประเภทรายการข้อมูลอิเล็กทรอนิกส์ที่นำมา Generate ที่ระบบ getInvoice คลิกที่  ![](<../../.gitbook/assets/image (224).png>) อธิบายดังตาราง

ตาราง ‎: อธิบาย Key-In Invoice

| สถานะ       | คำอธิบาย                                                                                                                                                  |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Non Key-In  | รายการข้อมูลอิเล็กทรอนิกส์ประเภท .xml, .csv, .xlsx, .txt ที่นำเข้าโดยผ่านช่องทาง zDOX, REST API, SFTP, Email ![](<../../.gitbook/assets/image (217).png>) |
| Key-In Only | รายการข้อมูลที่ทำการสร้างที่เมนู Create An Invoice เท่านั้น ![](<../../.gitbook/assets/image (228).png>)                                                  |

3\)       Dropdown list ตัวเลือกสำหรับกำหนดค้นหาข้อมูล ได้แก่ Document No., Buyer Name, Tax ID และ Source

<figure><img src="../../.gitbook/assets/image (279).png" alt=""><figcaption><p>Send to RD – ตัวเลือกสำหรับกำหนดค้นหาข้อมูล</p></figcaption></figure>

4\) กรองข้อมูลตามสาขา หรือแผนก หากมีบริษัทมีหลายสาขา สามารถกรองข้อมูลตามสาขา หรือ แผนกได้ โดยเลือกที่สัญลักษณ์ <img src="../../.gitbook/assets/image (10).png" alt="" data-size="line"> จากนั้นเลือกกรอง Department จากนั้นเลือกแผนก หรือ สาขา ที่ต้องการ

<mark style="color:purple;">(กรณีไม่มีแผนก หรือ สาขา Filter จะไม่ปรากฎหัวข้อ Department)</mark>

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Send to RD - วิธีการเลือกตัวกรอง</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Send to RD - เลือก Department ใน Filter</p></figcaption></figure>
