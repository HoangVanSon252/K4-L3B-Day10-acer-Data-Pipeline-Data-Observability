# Danh Sách Thành Viên & Báo Cáo Phân Công Nhóm

- **Tên nhóm:** `acer`
- **Mã nhóm / Lớp:** `K4-L3B-DAY10`
- **Repository:** `K4-L3B-Day10-acer-Data-Pipeline-Data-Observability`

## Thành viên

| STT | Họ và tên | MSSV | Email | Vai trò & phạm vi chính | Báo cáo cá nhân |
|---:|---|---|---|---|---|
| 1 | Hoàng Văn Sơn | 2A202602375 | 26ai.sonhv@vinuni.edu.vn | Trưởng nhóm; ingestion, cleaning, orchestration và recovery | `report/2A202602375_HoangVanSon.md` |
| 2 | Nguyễn Hữu Chương | 2A202602601 | huuchuonghtra@gmail.com | RAG, embedding, ChromaDB, observability và tích hợp pipeline | `report/2A202602601_NguyenHuuChuong.md` |
| 3 | Phạm Quốc Đạt | 2A202602384 | datkcr007@gmail.com | Benchmark evaluation và synthetic data corruption | `report/2A202602384_PhamQuocDat.md` |

## Phân công và bằng chứng

### Hoàng Văn Sơn — Data Foundation & Pipeline Integration

- Hoàn thiện ingestion Crossref và offline fallback trong `src/ingestion/crossref.py`.
- Chuẩn hóa dữ liệu, tính `age_days` và tạo `text_for_embedding` trong `src/ingestion/cleaning.py`.
- Điều phối `src/pipelines/phase1.py` và `src/pipelines/corruption_flow.py`.
- Bằng chứng: raw/clean artifacts, baseline pipeline và repaired dataset.

### Nguyễn Hữu Chương — RAG, Vector Store & Observability

- Xây dựng embedding/index với `all-MiniLM-L6-v2` và ba collection ChromaDB.
- Hoàn thiện GX 1.x Quality Gate, Freshness SLA và báo cáo pipeline.
- Hỗ trợ tích hợp, chạy và đối chiếu ba trạng thái baseline/corrupted/repaired.
- Bằng chứng: `data/embeddings/`, `data/chroma/`, `data/quality/` và `data/reports/`.

### Phạm Quốc Đạt — Evaluation & Corruption

- Xây dựng test set 10 câu hỏi thuộc bốn nhóm `summary`, `authors`, `date`, `categories`.
- Triển khai sáu kịch bản corruption và tái tạo `text_for_embedding` sau biến đổi.
- Bằng chứng: `data/eval/test_set.json`, `data/results/corruption_log.json` và corrupted metrics.

## Contract tích hợp chung

- Raw source of truth: `data/raw/crossref_records.json`.
- Document identity: DOI trong trường `paper_id`.
- Cùng một test set được dùng cho baseline, corrupted và repaired.
- Repair luôn tái tạo clean dataframe từ raw snapshot, không vá trực tiếp dữ liệu corrupted.
- Các số liệu báo cáo phải khớp với artifacts trong `data/results/` và `data/quality/`.
