# PyThaiNLP
[![Build Status](https://travis-ci.org/wannaphongcom/pythainlp.svg?branch=master)](https://travis-ci.org/wannaphongcom/pythainlp)
[![Documentation Status](https://readthedocs.org/projects/pythainlp/badge/?version=latest)](http://pythainlp.readthedocs.io/en/latest/?badge=latest)

Thai NLP in python package. 

Natural language processing หรือ การประมวลภาษาธรรมชาติ  โมดูล PyThaiNLP เป็นโมดูลที่ถูกพัฒนาขึ้นเพื่องานวิจัยและพัฒนา การประมวลภาษาธรรมชาติในภาษา Python

รองรับเฉพาะ Python 3 เท่านั้น (Python 2 กำลังพัฒนา)

### Version
0.0.5

### มีอะไรใหม่
ปรับปรุงประสิทธิภาพ ย้ายโค้ดบางส่วนไปใช้ NLTK

### ความสามารถ
  - ตัดคำภาษาไทย
  - Postaggers ภาษาไทย
  - อ่านตัวเลขเป็นข้อความภาษาไทย
  - เรียงจำนวนคำของประโยค
  - แก้ไขปัญหาการพิมพ์ลืมเปลี่ยนภาษา
  - และอื่น ๆ 

# ติดตั้ง

รองรับเฉพาะ Python 3

รุ่นเสถียร
```sh
$ pip3 install pythainlp
```
รุ่นกำลังพัฒนา
```sh
$ git clone https://github.com/wannaphongcom/pythainlp.git
$ cd pythainlp
$ python setup.py install
```

# เอกสารการใช้งานเบื้องต้น

ตัวอย่างการใช้งาน
```python
# ตัดคำ
from pythainlp.segment import segment
a = 'ฉันรักภาษาไทยเพราะฉันเป็นคนไทย'
b = segment(a)
print(b) # ['ฉัน', 'รัก', 'ภาษาไทย', 'เพราะ', 'ฉัน', 'เป็น', 'คนไทย']
# Postaggers ภาษาไทย
from pythainlp.postaggers import tag
print(tag('คุณกำลังประชุม')) # [('คุณ', 'PPRS'), ('กำลัง', 'XVBM'), ('ประชุม', 'VACT')]
# หาคำที่มีจำนวนการใช้งานมากที่สุด
from pythainlp.rank import rank
aa = rank(b)
print(aa) # Counter({'ฉัน': 2, 'ไทย': 2, 'เป็น': 1, 'รัก': 1, 'ภาษา': 1, 'เพราะ': 1, 'คน': 1})
# ทับศัพท์เสียงไทยในภาษาอังกฤษ (ยังไม่รองรับเสียงสระ)
from pythainlp.romanization import romanization
b=romanization("ต้นกก")
print(b) # tonkok
# แก้ไขปัญหาการพิมพ์ลืมเปลี่ยนภาษา
from pythainlp.change import *
a="l;ylfu8iy["
a=texttothai(a)
b="นามรสนอำันี"
b=texttoeng(b)
print(a) # สวัสดีครับ
print(b) # ok,iloveyou
# เปลี่ยนตัวเลขเป็นตัวอักษรภาษาไทย (เงินบาท)
from pythainlp.number import numtowords
print("5611116.50")
print(numtowords(5611116.50)) # ห้าล้านหกแสนหนึ่งหมื่นหนึ่งพันหนึ่งร้อยสิบหกบาทห้าสิบสตางค์
```

### License

Apache Software License 2.0

พัฒนาโดย นาย วรรณพงษ์  ภัททิยไพบูลบ์