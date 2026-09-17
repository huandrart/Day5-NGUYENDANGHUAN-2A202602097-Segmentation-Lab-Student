# REPORT.md --- Day 5 Segmentation Data Lab

* Mã học viên theo lớp: **2A202602097**
* Ngày / CVAT local: **17/09/2026 / CVAT local**
* Công cụ đã dùng: **Polygon**

## 1\. Bài đã nộp

\---

Task              File ZIP đúng tên         Hoàn thành mấy ảnh   Điểm tối đa (coach
chấm sau)

\---

easy\_semantic     `easy\_semantic.zip`                    3 / 3                   20

medium\_instance   `medium\_instance.zip`                  3 / 3                   32

hard\_panoptic     `hard\_panoptic.zip`                    2 / 2                   30

cp1\_holes         `cp1\_holes.zip`                        1 / 1                    3

cp2\_slice         `cp2\_slice.zip`                        1 / 1                    3

cp5\_occlusion     `cp5\_occlusion.zip`                    1 / 1                    3

cp3\_thin          `cp3\_thin.zip`                         1 / 1                    3

cp4\_curb          `cp4\_curb.zip`                         1 / 1                    3

cp6\_coverage      `cp6\_coverage.zip`                     1 / 1                    3

## **Tổng tối đa**                                                             **100**

## 2\. Một quyết định trước khi dùng gợi ý

* **Ảnh, vị trí và object Medium đầu tiên tự vẽ:** Object
`PERSON 1 (MANUAL)`, class `person`. Đây là người phụ nữ đứng gần
trung tâm ảnh, hơi lệch về bên trái, mặc trang phục sáng màu.
* **Class và quy tắc tôi dùng để chọn biên:** Class `person`. Tôi dùng
Polygon và đặt các điểm theo đường viền phần cơ thể thực sự nhìn
thấy, bám sát ranh giữa người với nền và các phương tiện xung quanh.
Tôi không mở rộng vùng gán nhãn sang xe hoặc nền và không tự suy
đoán phần cơ thể bị che.
* **Nếu dùng gợi ý sau đó:** Không dùng gợi ý tự động/SAM. Object được
vẽ thủ công bằng Polygon và tôi kiểm tra lại biên trước khi Save.

## 3\. Một lỗi tôi tìm thấy và sửa

* **Task/ảnh/vùng:** `medium\_instance` --- ảnh `000000458325.jpg` ---
Object 65.
* **Lỗi thuộc loại:** thiếu vật / thiếu annotation.
* **Bằng chứng tôi nhìn thấy:** Khi kiểm tra lại ảnh, tôi phát hiện
một người có thể quan sát được trong ảnh nhưng trước đó chưa có
annotation tương ứng.
* **Quy tắc và hành động sửa:** Tôi bổ sung Object 65, gán class
`person` và dùng Polygon để vẽ theo phần cơ thể thực sự nhìn thấy.
Tôi không suy đoán phần bị che và kiểm tra để polygon không tràn
sang nền hoặc vật thể xung quanh.
* **Sau sửa đã Save và export lại chưa?** Có. Tôi đã Save annotation
sau khi sửa và export lại `medium\_instance.zip`.
* **Kết quả tự đánh giá liên quan lỗi sau khi sửa:** Chưa ghi điểm vào
report; điểm chính thức do công cụ/người phụ trách chấm.

## 4\. Ba ca chưa chắc hoặc đã cân nhắc

\---

Ảnh/vị trí            Hai cách hiểu có  Quy tắc/chứng cứ  Quyết định hoặc
thể                                 câu hỏi cho coach

\---

`medium\_instance` --- Bỏ qua vì người   Tôi kiểm tra ở    Tôi chọn gán
ảnh                   nhỏ, khó thấy /   mức zoom lớn hơn  `person` riêng và
`000000458325.jpg`,   vẫn tạo một       và dựa vào phần   chỉ vẽ phần nhìn
người ở xa/nhỏ trong  instance `person` hình dáng cơ thể  thấy
cảnh                  vì vẫn nhận ra    còn quan sát  
được người        được. Quy tắc là  
gán phần vật thể  
thực sự nhìn  
thấy, không tự  
suy đoán phần bị  
che

Ảnh đường phố nhiều   Không gán vì kích Khi zoom ảnh,     Tôi chọn gán
làn --- người ở xa    thước rất nhỏ /   hình dáng người   `person` và bám
trong ảnh             gán `person` vì   vẫn tách được     polygon theo phần
hình dáng người   khỏi nền và có    nhìn thấy
vẫn có thể nhận   thể xác định là  
biết              một người

Ảnh đường phố nhiều   Xem vùng đó như   Tôi xem xét cấu   Tôi chọn gán
làn --- xe đạp ở      một phần của      trúc nhìn thấy    `bicycle` thành
xa/khó quan sát       người/vật gần đó  của xe và nguyên  một instance
/ tạo instance    tắc các vật thể   riêng khi cấu
`bicycle` riêng   đếm được cùng lớp trúc xe còn nhận
phải là instance  biết được
riêng; không gộp  
hai vật thể khác  
nhau chỉ vì chúng
nằm gần nhau
---

