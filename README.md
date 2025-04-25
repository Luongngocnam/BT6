
# Bài tập 6: Hệ quản trị CSDL
Chủ đề: Câu lệnh Select
Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

DEADLINE: 23H59:59 NGÀY 25/4/2025

Ghi chú: Giải thích tại sao lại có SQL như vậy.
# Bài làm
## 1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
- Vào phần File >> Open >> Files >> chọn file sv_tnut.sql đã tải từ thầy trước đó.
  ![image](https://github.com/user-attachments/assets/92e84eb2-2cac-40e1-9c99-cfaa21b5abbe)
  ![image](https://github.com/user-attachments/assets/486852d0-f858-46b3-b687-a5ee88049dda)
## 2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
- Sau khi chạy file sv_tnut.sql của thày ta được bảng dữ liệu dài 9000 dòng như sau:
  ![Ảnh chụp màn hình 2025-04-25 150935](https://github.com/user-attachments/assets/754f710d-1aef-4d8e-9755-d7a8eab9607f)
## 3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em? 
Dùng lệnh select để lấy các trường thuộc tính có trong bảng dbo.SV.  
Và sử dụng lệnh Where để tìm những người có cùng ngày tháng năm sinh với em.  
![image](https://github.com/user-attachments/assets/59d78f31-34ef-4555-8dd8-fcecb5f42fba)  
```
Select * From dbo.SV
Where ns = '2004-08-07'
```
## 4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em? 
Khác với câu trên câu này em thay đổi việc tìm kiếm đầy đủ ngày tháng năm sinh bằng việc tìm những người có cúng ngày sinh và tháng sinh.  
![image](https://github.com/user-attachments/assets/e916cfcf-5ee5-490b-bcdf-e1e922893b28)
```
Where Day(ns) = 08 AND Month(ns) = 10;
```
## 5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?  
Giống với câu 4, nhưng câu này em chỉ việc tìm kiếm các dữ liệu giống năm sinh thay cho việc tìm kiếm ngày sinh. 
![image](https://github.com/user-attachments/assets/7b240add-5ad6-4338-aaf7-1a41b4f814d9)
## 6. nhập sql để tìm xem có những sv nào trùng tên với em? 
Thay thế việc tìm kiếm ngày sinh thành tìm kiếm tên.
![image](https://github.com/user-attachments/assets/c830df22-1d2f-49b9-b4bd-64e5a3547321)  
## 7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.  
Thay thế thành tìm họ đệm.
![image](https://github.com/user-attachments/assets/ce15f617-3aa5-45c1-9fc9-80036dc6b28c)
## 8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.  
Sử dụng hàm lệnh Case When SubString để so sánh từng kí tự số trong sdt của em và kiểm tra xem có ai có số điện thoại chỉ khác 1 số (ký tự số).
![Ảnh chụp màn hình 2025-04-25 153551](https://github.com/user-attachments/assets/3b50f6c4-eb2c-4061-acab-ed0804fb12d5)
```
Where (
    (Case When SubString(sdt,1,1) <> SubString('0393541400',1,1) Then 1 Else 0 End +
     Case When SubString(sdt,2,1) <> SubString('0393541400',2,1) Then 1 Else 0 End +
     Case When SubString(sdt,3,1) <> SubString('0393541400',3,1) Then 1 Else 0 End +
     Case When SubString(sdt,4,1) <> SubString('0393541400',4,1) Then 1 Else 0 End +
     Case When SubString(sdt,5,1) <> SubString('0393541400',5,1) Then 1 Else 0 End +
     Case When SubString(sdt,6,1) <> SubString('0393541400',6,1) Then 1 Else 0 End +
     Case When SubString(sdt,7,1) <> SubString('0393541400',7,1) Then 1 Else 0 End +
     Case When SubString(sdt,8,1) <> SubString('0393541400',8,1) Then 1 Else 0 End +
     Case When SubString(sdt,9,1) <> SubString('0393541400',9,1) Then 1 Else 0 End +
     Case When SubString(sdt,10,1) <> SubString('0393541400',10,1) Then 1 Else 0 End)
) = 1
```
## 9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
![image](https://github.com/user-attachments/assets/1cf9db58-bbfb-4f63-818c-bcc192e80152)

``` WHERE lop LIKE '%KTP%' ```
Được dùng để lọc ra các thông tin có chứa ký tự liên quan đến KTP.
```ORDER BY 
    ten COLLATE Vietnamese_CI_AS, 
    hodem COLLATE Vietnamese_CI_AS; 
```
Được dùng để sắp xếp theo tên và họ đệm thay vì sắp xếp theo các trình tự khác và Vietnamese_CI_AS để định dạng kiểu tiếng việt.
## 10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)
![image](https://github.com/user-attachments/assets/11cd2a1d-d70c-472b-a1e1-d46ada49f951)
Cách này chỉ tìm được những tên mà mình đã nhập.
## Giải thích tại sao lại có SQL như vậy.  
SQL như này được tạo ra nhằm quản lý thông tin của sinh viên trong trường.





