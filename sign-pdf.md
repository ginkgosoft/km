# Sign PDF

ผู้ใช้งานสามารถส่งไฟล์ PDF มาที่ระบบ getInvoice เพื่อลงลายมือชื่อดิจิทัลได้ (Digital Signatures) ซึ่งผู้ใช้งานจะต้องมี Control File (.csv) เพื่อเป็นเอกสารที่บ่งบอกว่าผู้ใช้จะนำเข้า PDF ไฟล์ไหนบ้าง คอลัมน์ที่แสดงใน Control File อธิบายดังตาราง

ตาราง : อธิบายการกรอกข้อมูล Control File

| คอลัมน์           | คำอธิบาย                                          |
| ----------------- | ------------------------------------------------- |
| PDF\_NAME         | ชื่อไฟล์ PDF ที่ต้องการนำเข้าระบบ getInvoice      |
| DOCUMENT\_TYPE    | ประเภทเอกสาร                                      |
| DOCUMENT\_NO      | เลขที่เอกสาร                                      |
| DOCUMENT\_DATE    | วันที่ออกเอกสาร                                   |
| SELLER\_EMAIL     | อีเมลของผู้ขาย                                    |
| SELLER\_TELEPHONE | เบอร์โทรศัพท์ของผู้ขาย                            |
| BUYER\_NAME       | ชื่อผู้ซื้อ                                       |
| BUYER\_EMAIL      | อีเมลของผู้ซื้อ                                   |
| BUYER\_TELEPHONE  | เบอร์โทรศัพท์ของผู้ซื้อ                           |
| PDF\_PATH         | Path สำหรับจัดเก็บเอกสาร PDF บน zDOX              |
| OUTPUT\_FILENAME  | ชื่อไฟล์ของเอกสาร PDF ที่จัดเก็บบน zDOX หรือ SFTP |

เมื่อผู้ใช้งานวางไฟล์ตามช่องทางที่กำหนดจะต้องวางไฟล์ PDF และ Control File แนบมาพร้อมกัน โดยชื่อเอกสาร PDF จะต้องมีชื่อตรงกับข้อมูลในคอลัมน์ PDF\_NAME เท่านั้น ระบบนำเข้าไฟล์สำเร็จแสดงไอคอน ![](<.gitbook/assets/image (332).png>) ถ้าผู้ใช้งานวางไฟล์ PDF ไม่ตรงกับข้อมูลในคอลัมน์ PDF\_NAME เมื่อเข้าระบบ getInvoice จะแสดง ไอคอน ![](<.gitbook/assets/image (353).png>)

<figure><img src=".gitbook/assets/image (390).png" alt=""><figcaption><p>ตัวอย่างการวางไฟล์ PDF และ Control File</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (395).png" alt=""><figcaption><p>หน้าจอ Jobs – นำเข้าไฟล์ PDF สำเร็จ</p></figcaption></figure>

ผู้ใช้งานสามารถคลิกดู Transactions ได้

<figure><img src=".gitbook/assets/image (343).png" alt=""><figcaption><p>หน้าจอ Jobs – ดูข้อมูล Transactions</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (348).png" alt=""><figcaption><p>หน้าจอ Jobs – นำเข้าไฟล์ PDF ไม่สำเร็จ</p></figcaption></figure>

ผู้ใช้งานสามารถคลิกดู Error ของ Transactions ได้

<figure><img src=".gitbook/assets/image (379).png" alt=""><figcaption><p>หน้าจอ Jobs – ดูข้อมูล Error ของ Transactions</p></figcaption></figure>
