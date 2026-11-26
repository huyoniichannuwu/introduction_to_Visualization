QUY ƯỚC CHUNG - BÀI TRỰC QUAN HÓA (cả nhóm dùng thống nhất) - NHÓM 7 [012012710603]

1. NGUỒN DỮ LIỆU
- Tất cả chỉ đọc file Amazon_clean.csv do nhóm trưởng làm sạch rồi chia sẻ. (Amazon_clean.csv)
- KHÔNG ai tự làm sạch hay sửa dữ liệu riêng, để số liệu giữa các slide không lệch nhau.
- Dataset gốc (Amazon_raw.csv): 100.000 dòng, 20 cột, mỗi dòng là 1 đơn hàng.

2. DOANH THU
- Doanh thu = tổng TotalAmount của các đơn có OrderStatus KHÔNG phải Cancelled hoặc Returned.
- Các đơn Delivered, Shipped, Pending đều được tính.
- Mọi biểu đồ về doanh thu đều dùng định nghĩa này.
- Tiêu đề biểu đồ ghi rõ "Doanh thu (không gồm đơn hủy, trả)".

3. TỈ LỆ HỦY / TRẢ
- Tỉ lệ hủy = số đơn Cancelled / tổng số đơn.
- Tỉ lệ trả = số đơn Returned / tổng số đơn.

- Tổng số đơn (mẫu số) tính ĐỦ mọi trạng thái, kể cả Cancelled và Returned.
- Ghi chú: doanh thu loại đơn hủy/trả, nhưng tỉ lệ thì phải tính trên tất cả đơn, nếu không sẽ sai.

4. NGƯỠNG TỐI THIỂU (câu 9) - bỏ qua vì các sản phẩm đều từ 1910 trở lên cho đến 2098
- MIN_ORDERS = 1900 đơn/sản phẩm.
- Lý do: mỗi sản phẩm có khoảng 1910 đến 2098 đơn nên mọi sản phẩm đều đủ điều kiện.

5a. ĐỊA LÝ
- Dữ liệu Country không khớp với State/City (mỗi State xuất hiện ở cả 5 Country), nhiều khả năng do dữ liệu mô phỏng.
- Câu 5 dùng Country. Câu 7 dùng State.
- KHÔNG ghép Country với State hoặc City trong cùng 1 biểu đồ.
- Slide "Hạn chế" ghi 1 dòng về điểm này.

5b. CATEGORY
- Category không khớp với ProductName (mỗi sản phẩm xuất hiện ở cả 6 Category), nhiều khả năng do dữ liệu mô phỏng.
- Câu 4, 6 dùng Category. Câu 9 dùng ProductName.
- KHÔNG ghép Category với ProductName trong cùng 1 biểu đồ hay nhận xét.
- Câu 4: Category chỉ có 6 giá trị nên vẽ đủ 6 nhóm (không có top 10).
- Slide "Hạn chế" ghi thêm 1 dòng về điểm này.

6. THỜI GIAN
- OrderDate đổi sang kiểu ngày (pd.to_datetime).
- df_clean có sẵn cột Year và Month cho câu 2.

7. QUY CÁCH SLIDE (mỗi câu hỏi 1 slide, cùng khuôn)
- Câu hỏi là gì -> Biểu đồ nào, vì sao chọn loại này -> Nhìn thấy gì.
- Mỗi slide có 1 câu nhận xét kết luận.
- Gộp theo cụm: Câu 1-3 (tổng quan), 4-6 (nhóm sản phẩm, khu vực), 7-9 (đi sâu), 10 (dashboard + 3 đề xuất).

8. KẾT QUẢ LÀM SẠCH (đã chốt)
- 100.000 dòng, không thiếu, không trùng, không lỗi ngày, không giá trị vô lý.
- TotalAmount khớp công thức Quantity x UnitPrice x (1 - Discount) + Tax + ShippingCost (sai số làm tròn tối đa 0,005).
- Ngày từ 2020-01-01 đến 2024-12-29. Nhãn Category, PaymentMethod, Brand không bị lặp.
