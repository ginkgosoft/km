# Review Invoice กำหนดจำนวนและลำดับผู้อนุมัติ

ผู้ดูแลระบบจะสามารถกำหนดจำนวนและลำดับผู้อนุมัติงานได้สูงสุด 5 ระดับ ตัวอย่างเช่น กำหนดให้มีผู้อนุมัติ 3 ระดับ เมื่อมีการนำเข้ารายการใบกำกับภาษีอิเล็กทรอนิกส์หรือใบรับอิเล็กทรอนิกส์เรียบร้อยแล้ว รายการจะมาแสดงที่เมนู Review Invoice สถานะ To Review ของผู้อนุมัติลำดับแรก

<figure><img src="../../.gitbook/assets/image (152).png" alt=""><figcaption><p>หน้าจอ Review Invoice - ผู้อนุมัติลำดับที่ 1</p></figcaption></figure>

**ผู้อนุมัติคนแรก:** เลือกรายการและกดปุ่ม Approve หรือ Approve All เรียบร้อยแล้ว รายการจะไปแสดงที่หน้าจอเมนู Review Invoice สถานะ To Review ของผู้อนุมัติลำดับที่ 2 ซึ่งถ้าผู้อนุมัติคนแรกยังไม่ได้ทำการ Approve รายการก็จะยังไม่แสดงในหน้าจอในสถานะ To Review ของผู้อนุมัติลำดับที่ 2

<figure><img src="../../.gitbook/assets/image (168).png" alt=""><figcaption><p>หน้าจอ Review Invoice – ผู้อนุมัติลำดับที่ 2</p></figcaption></figure>

**ผู้อนุมัติลำดับที่ 2:** เลือกรายการและกดปุ่ม Approve หรือ Approve All เรียบร้อยแล้ว รายการจะไปแสดงที่หน้าจอเมนู Review Invoice ของผู้อนุมัติลำดับที่ 3 สถานะ To Review ซึ่งถ้าผู้อนุมัติลำดับที่ 2 ยังไม่ได้ Approve รายการก็จะยังไม่แสดงในหน้าจอของผู้อนุมัติลำดับที่ 3 ที่สถานะ To Review

<figure><img src="../../.gitbook/assets/image (138).png" alt=""><figcaption><p>หน้าจอ Review Invoice - ผู้อนุมัติลำดับที่ 3</p></figcaption></figure>

**ผู้อนุมัติลำดับที่ 3:** เลือกรายการและกดปุ่ม Approve หรือ Approve All รายการจะไปแสดงที่หน้าจอเมนู Send to Buyer (ดังรูป) และ Send to RD (ดังรูป)

<figure><img src="../../.gitbook/assets/image (104) (1).png" alt=""><figcaption><p>หน้าจอ Send to Buyer – แสดงรายการอนุมัติครบตามลำดับที่กำหนด</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption><p>หน้าจอ Send to RD – แสดงรายการอนุมัติครบตามลำดับที่กำหนด</p></figcaption></figure>

กรณี Reject หรือ Reject All รายการใบกำกับภาษีอิเล็กทรอนิกส์และใบรับอิเล็กทรอนิกส์จะยังแสดงอยู่กับผู้อนุมัติที่กด Reject ลำดับปัจจุบัน ซึ่งผู้อนุมัติสามารถกดปุ่ม Disreject ได้ที่สถานะ Rejected ส่วนรายการที่ถูก Reject ไปแล้วจะไม่แสดงที่เมนู Send to Buyer และ Send to RD

<figure><img src="../../.gitbook/assets/image (163).png" alt=""><figcaption><p>หน้าจอ Review Invoice – ผู้อนุมัติทำการ Reject</p></figcaption></figure>
