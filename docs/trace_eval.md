# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Trần Phạm Thái Vũ  
> **Mã Sinh Viên / Mã Học viên:** 2A202602695  
> **Chủ đề Lựa chọn:** Gợi ý 1.1 — Trợ lý Học vụ & Tra cứu Lịch hẹn VinUni (VinUni Academic Assistant)  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 5 / 5 | Tác vụ đặt lịch tư vấn yêu cầu chuỗi suy luận đa bước: (1) Tra cứu hồ sơ sinh viên để xác định Cố vấn học tập được phân công $\rightarrow$ (2) Dùng thông tin cố vấn đó để tiến hành đặt lịch hẹn. |
| **2. Tool Interaction** | 5 / 5 | Dữ liệu học vụ (GPA, Cố vấn, lịch hẹn) mang tính chất động, bảo mật và thay đổi liên tục, bắt buộc phải truy xuất qua Tool kết nối MCP Server / Cơ sở dữ liệu trường để tránh ảo giác (hallucination). |
| **3. Dynamic Decision** | 4 / 5 | Phản hồi của Agent phụ thuộc vào kết quả Observation từ Tool: Nếu tìm thấy sinh viên thì trích xuất Cố vấn để hẹn lịch; nếu mã sinh viên không tồn tại (`NOT_FOUND`), Agent phải dừng chuỗi đặt lịch và phản hồi lỗi chính xác. |
| **4. Long Horizon Goal** | 4 / 5 | Hệ thống duy trì mục tiêu của người dùng (hẹn lịch tư vấn thành công) qua nhiều bước gọi công cụ và tổng hợp kết quả mà không bị mất ngữ cảnh. |
| **TỔNG ĐIỂM AGENTIC FIT** | **18 / 20** | *Kết luận: Đạt 18/20 (> 12/20), bài toán hoàn toàn phù hợp và cần thiết để triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "class": "AI-K4",
        "gpa": 3.85,
        "email": "an.nv@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 2125.27
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Kết quả tra cứu cho sinh viên SV2026001 (Nguyễn Văn An): Lớp AI-K4, GPA: 3.85, Email: an.nv@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: PGS.TS Nguyễn Văn A.",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 4 lượt (TC02, TC03, TC04, TC05; riêng TC01 trả lời trực tiếp không gọi tool).
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
