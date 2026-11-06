# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM


- **MSSV:** 2A202603974
- **Họ và tên:** Khổng Ngọc Anh
- **SEED** (in ở ô đầu notebook): 1646

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | Có |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | Có |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | Có |

## 2. Kết quả chính

| Method                         | F1    | F1_SUB |
|--------------------------------|-------|--------|
| 1. BoW + LogReg (tự code)       | 0.859 | 0.889  |
| 2. BoW + MLP (deep learning)    | 0.944 | 0.974  |
| 3a. Encoder (MiniLM) + kNN      | 0.909 | 0.895  |
| 3b. Encoder (MiniLM) + LogReg   | 0.978 | 1.000  |
| 3c. Encoder (MiniLM) + MLP head | 0.967 | 0.974  |
| 4a. LLM nhỏ zero-shot           | 0.927 | 0.927  |
| 4b. LLM lớn zero-shot           | 0.974 | 0.974  |
| 4c. LLM nhỏ few-shot            | 0.950 | 0.950  |

## 3. Dự đoán và thực tế

Dự đoán: "hard_eval: sẽ khoảng 90%"
- Thực tế: Trừ LLM, tất cả model đều tụt mạnh 
- Bài học: Một bộ test khó có thể thay đổi cách ta nhìn các phương pháppháp

## 4. Phân tích 50 case khó

Bag of Word tụt nhiều nhất. Bởi các câu đều né tránh các từ khoá spam phổ biến

## 5. Thử thách cá nhân

Đề: DL · Đổi lớp ẩn MLP thành 4 và 512 nơ-ron. Báo số tham số, F1 test, thời gian train. Khi nào nên chọn mạng nhỏ?
- Cách làm: Tận dụng pipeline đã có từ phần DL, chỉ thay đổi tham số khởi tạo mạng MLP
- Kết quả: hidden = 4 cho kết quả khá tốt với 8000 tham số, còn hidden = 512 cho kết quả rất tệ với 1 triệu tham số. 

## 6. Phương án cho sản phẩm thật

Dựa trên biểu đồ đánh đổi, nên chọn BoW + MLP, bởi phương pháp này cân bằng giữ tốc độ với độ hiệu quả, trong khi không tốn tiền như LLM 

## 7. AI log và điều đã học
