# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600424
**Name:** Tạ Vĩnh Phúc
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 10 | Agent tư vấn đúng món đồ điện tử hợp lý |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 0 | Agent bị lừa bởi dữ liệu tạp nham |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent lấy thông tin hoàn toàn dựa trên bộ dữ liệu được nạp vào, thiếu suy luận logic độc lập về thế giới thực nếu không được cấp đủ rule ngữ cảnh. Khi bộ dữ liệu bị "đầu độc" bằng các bản ghi chứa giá trị bất thường (outliers như $999999), hoặc những loại hàng hoá viễn tưởng/không tồn tại trên thị trường (Lò phản ứng hạt nhân, Nuclear Reactor), hệ thống Agent sẽ chỉ trích xuất thông tin một cách máy móc và ngây thơ. 

Nếu không có ETL, các vấn đề như dữ liệu rỗng (null values), giá trị âm/sai kiểu sẽ phá vỡ quy trình RAG của AI. Nó khiến Agent học sai và đưa ra các đề xuất hoàn toàn vô lý làm hỏng trải nghiệm người dùng cuối.

---

## 3. Ket luan

**Quality Data > Quality Prompt?**
Hoàn toàn đồng ý. Bất kể prompt có chi tiết hay kỹ thuật RAG phức tạp đến đâu, câu châm ngôn "Garbage In, Garbage Out" luôn đúng đối với AI và ML. Nếu dữ liệu đầu vào chứa toàn thông tin sai lệch, thiếu sót, hoặc không chuẩn hóa, kết quả sinh ra của mô hình cũng sẽ thất bại y hệt. Do đó bước quan trọng nhất trong việc phát triển ứng dụng AI chính là việc xây dựng hệ thống Data Pipeline ETL có tính Observability vững chắc ở tầng nền tảng.
