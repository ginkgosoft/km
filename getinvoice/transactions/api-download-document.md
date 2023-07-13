# API download document

สามารถ Download transaction ได้โดยใช้ API โดยมีกระบวนการดังต่อไปนี้

1. Get API download ตามลิงค์ [https://{domain}/eTax/api/content?key={api\_key}\&id={transaction\_id}](https://{domain}/eTax/api/content?key={api\_key}\&id={transaction\_id})&#x20;

|                   |                                           |
| ----------------- | ----------------------------------------- |
| หัวข้อ            | คำอธิบาย                                  |
| {domain}          | Domain ของ Corporate                      |
| {api\_key}        | API key ของ Corporate                     |
| {transaction\_id} | ID ของ Transaction ที่ระบุมาใน Input file |

1.1 {domain} ตัวอย่างตามภาพ

<figure><img src="../../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>ตัวอย่างภาพ Domain</p></figcaption></figure>

1.2 {api\_key}

Log in เข้าสู่ getInvoice จากนั้นเลือกแท็บ Dashboard จากนั้น เลือกที่ "API usage example"&#x20;

<figure><img src="../../.gitbook/assets/image (3) (3).png" alt=""><figcaption><p>ภาพวิธีค้นหา API</p></figcaption></figure>

จะปรากฎหน้าต่าง REST API  ให้ท่านคัดลอกข้อมูล X-API-KEY (ตามกรอบสีแดงในภาพ) เพื่อใช้เป็นข้อมูล {api\_key}

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>หน้าจอ  REST API  </p></figcaption></figure>

1.3 {transaction\_id}

ท่านสามารถดูได้จาก ID ของ Transaction ใน Input file
