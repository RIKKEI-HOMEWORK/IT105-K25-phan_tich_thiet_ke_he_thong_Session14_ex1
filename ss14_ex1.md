# BÀI LÀM: THỰC HÀNH THIẾT KẾ TÍNH NĂNG ĐÁNH GIÁ SẢN PHẨM RIKKEISHOP

## Bước 1: Phân tích Use Case & Xác định Yếu tố UI

### 1. Xác định Actor

* **Primary Actor (Tác nhân chính):** Khách hàng (Người dùng đã mua hàng trên RikkeiShop, có nhu cầu để lại phản hồi thực tế về sản phẩm).
* **System Actor (Tác nhân hệ thống):** Hệ thống RikkeiShop (Hiển thị form đánh giá, tiếp nhận dữ liệu và gửi phản hồi xác nhận thành công).

### 2. Bảng ánh xạ hành động sang thành phần UI

| STT | Hành động của Actor | Thành phần UI tương ứng (UI Element) | Mô tả & Đặc tính hiển thị |
| :--- | :--- | :--- | :--- |
| 1 | Chọn số sao (1–5 sao) | **Star Rating Component** (Thanh chọn sao đánh giá) | 5 biểu tượng hình ngôi sao có khả năng tương tác; khi người dùng nhấn hoặc di chuột sẽ chuyển màu (xám sang vàng cam) để phản ánh mức độ hài lòng trực quan. |
| 2 | Nhập tiêu đề ngắn | **Single-line Text Field / Input Field** (Ô nhập liệu văn bản 1 dòng) | Ô nhập ký tự ngắn gọn, có văn bản gợi ý (*Placeholder: "Tóm tắt cảm nhận của bạn về sản phẩm..."*) kèm giới hạn độ dài ký tự rõ ràng. |
| 3 | Nhấn "Gửi đánh giá" | **Primary CTA Button** (Nút hành động chính) | Nút bấm đặt ở cuối form, kích thước đủ lớn, màu sắc thương hiệu nổi bật: `[ GỬI ĐÁNH GIÁ ]`. |

---

## Bước 2: Vẽ Wireframe Theo Luồng (2 Khung)

### KHUNG 1 — Form "Viết đánh giá" đang mở

```
+-----------------------------------------------------------------------+
|  TRANG SẢN PHẨM: ÁO THUN POLO NAM CAO CẤP                             |
+-----------------------------------------------------------------------+
|  [★] VIẾT ĐÁNH GIÁ SẢN PHẨM                                           |
|                                                                       |
|  1. Mức độ hài lòng của bạn:                                          |
|     [ ★ ]  [ ★ ]  [ ★ ]  [ ★ ]  [ ☆ ]   (4/5 - Rất hài lòng)          |
|                                                                       |
|  2. Tiêu đề đánh giá:                                                 |
|  +-----------------------------------------------------------------+  |
|  | Vải cotton mềm mát, form áo chuẩn đẹp!                          |  |
|  +-----------------------------------------------------------------+  |
|                                                                       |
|  +-----------------------------------------------------------------+  |
|  |                        ★  GỬI ĐÁNH GIÁ                          |  |
|  +-----------------------------------------------------------------+  |
|  (Nút Primary CTA: Màu sắc nổi bật, độ tương phản cao, dễ tương tác)  |
+-----------------------------------------------------------------------+
```

* **Đặc điểm thiết kế:**
  * Bố cục tinh gọn, chỉ tập trung vào 2 trường dữ liệu theo đúng Use Case.
  * Phân cấp thị giác rõ ràng, nút "Gửi đánh giá" có diện tích lớn giúp người dùng thao tác nhanh chóng và thuận tiện.

---

### KHUNG 2 — Màn hình sau khi nhấn "Gửi đánh giá" (Có xác nhận thành công)

```
+-----------------------------------------------------------------------+
|  TRANG SẢN PHẨM: ÁO THUN POLO NAM CAO CẤP                             |
+-----------------------------------------------------------------------+
|                                                                       |
|  +-----------------------------------------------------------------+  |
|  |  ✅  GỬI ĐÁNH GIÁ THÀNH CÔNG!                                   |  |
|  |                                                                 |  |
|  |  Cảm ơn bạn đã đóng góp ý kiến. Đánh giá của bạn đã được        |  |
|  |  ghi nhận và sẽ hiển thị công khai trên trang sản phẩm.         |  |
|  +-----------------------------------------------------------------+  |
|                                                                       |
|  +-----------------------------------------------------------------+  |
|  |                     XEM ĐÁNH GIÁ CỦA BẠN                        |  |
|  +-----------------------------------------------------------------+  |
|                                                                       |
+-----------------------------------------------------------------------+
```

* **Đặc điểm thiết kế:**
  * Thay thế form nhập liệu bằng thông báo trạng thái thành công (**Success Banner/Card**).
  * Sử dụng biểu tượng tích xanh `✅` cùng thông điệp cảm ơn rõ ràng nhằm mang lại sự an tâm tuyệt đối cho người mua.

---

## Bước 3: Tinh chỉnh theo Nguyên tắc UI (Feedback & Good UI / Bad UX)

**Câu hỏi:** Đối chiếu Khung 2 với nguyên tắc Feedback: nếu chỉ đóng form mà không có thông báo gì, tính năng này rơi vào Good UI hay Bad UX? Giải thích trong 1-2 câu.

**Trả lời:**

> Tính năng này rơi vào **Bad UX** (Trải nghiệm người dùng kém). 
> 
> Việc đột ngột đóng form mà thiếu phản hồi hệ thống (**System Feedback**) vi phạm nguyên tắc Usability cơ bản, khiến người dùng hoang mang không biết đánh giá đã gửi thành công hay bị lỗi mạng, từ đó có xu hướng bấm gửi lại nhiều lần gây trùng lặp dữ liệu.