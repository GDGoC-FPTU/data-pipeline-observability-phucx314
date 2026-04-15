[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574018&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** tavinhphuc123@gmail.com
**Name:** Tạ Vĩnh Phúc

---

## Mo ta

Bài lab xây dựng một pipeline ETL đơn giản thực hiện các bước:
- **Extract**: Đọc dữ liệu thô từ file JSON.
- **Validate**: Làm sạch dữ liệu, loại bỏ các bản ghi có giá trị lỗi (giá <= 0, thiếu Category).
- **Transform**: Khấu trừ giá (giảm 10%), chuẩn hóa tên Category và thêm siêu dữ liệu (thời gian xử lý).
- **Load**: Lưu kết quả dữ liệu sạch ra định dạng CSV để dùng cho AI Agent.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# 1. Tạo file dữ liệu rác
python generate_garbage.py

# 2. Chạy file mô phỏng AI Agent để kiểm tra cách bot phản hồi với 2 loại dữ liệu: sạch và rác
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Pipeline khởi chạy với file `raw_data.json`.
- **Validation** đã giữ lại 3 bản ghi chuẩn.
- Đã loại bỏ 2 bản ghi bị lỗi (`Price <= 0` và `Missing Category`).
- Tất cả 3 bản ghi đã được xử lý (transform category title case, tính thêm giá trị `discounted_price` giảm 10%, thêm timestamp `processed_at`) và lưu thành công ra `processed_data.csv`.
- AI Agent sau đó sử dụng dữ liệu sạch này để tư vấn mua sắm hợp lý.
