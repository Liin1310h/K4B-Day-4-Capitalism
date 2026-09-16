# TEAM — Day04, K4-L3B

**Làm nhóm.** Mỗi người tự viết và commit phần INDIVIDUAL của mình.

## Thông tin bài nộp

- Tên nhóm: Capitalism
- Người đại diện / MSSV:
- Tên repo: `K4-L3-DAY04-HoVaTen-MSSV-PromptEngineeringToolCalling`
- URL repo, nhánh nộp, commit chốt:
- Deadline áp dụng và link thông báo đổi hạn nếu có:

## Thành viên

| Họ và tên          | MSSV        | GitHub     | Vai trò và công việc                                                                                                     | File/commit/PR                                                                                                                                                    |
| ------------------ | ----------- | ---------- | ------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Phạm Thị Thùy Linh | 2A202602909 | Liine1310h | Prompt và tool contract: cải thiện system prompt, tool schema, routing, clarification và confirmation boundary | [system_prompt.md](starter_v0/artifacts/system_prompt.md), [tools.yaml](starter_v0/artifacts/tools.yaml), [version_log.csv](starter_v0/artifacts/version_log.csv) |
| Nguyễn Thị Lê Na | 2A202602501 | LeeNa0909   | UI và transcript: xây dựng giao diện chat Streamlit, hiển thị tool trace và lưu hội thoại | [app.py](starter_v0/app.py), [requirements.txt](starter_v0/requirements.txt), [transcripts](starter_v0/transcripts/) |

## Nhận xét chung

- Kết quả và bằng chứng:
- Thay đổi hiệu quả nhất:
- Giới hạn còn lại:
- Cách phân công và tích hợp:

## INDIVIDUAL

### Phạm Thị Thùy Linh — 2A202602909

- Phần việc và file/commit/PR: Phụ trách prompt và tool contract trong [system_prompt.md](starter_v0/artifacts/system_prompt.md) và [tools.yaml](starter_v0/artifacts/tools.yaml). Đã giữ nguyên tên tool, parameter và enum của registry; evidence chạy cùng bộ `data/eval_base.json` được lưu trong [runs](starter_v0/runs/). Commit riêng cho phần artifact: 277c270.
- Quyết định, khó khăn và cách xử lý: Bổ sung mapping service/device/KB/user/policy/external web; yêu cầu `clarify` khi thiếu ID hoặc environment; buộc chọn đúng `category`, `check`, `response_type`; ngăn employee ID bị dùng như asset ID; và chỉ tạo ticket sau xác nhận `yes_no` hiện tại cho đúng summary, priority và asset ID. Khó khăn chính là model vẫn tự map `demo/QA` sang `staging`, nên thêm rule phủ định rõ cho `demo`, `QA`, `test` và team name. Kết quả cuối đạt 30/30, provider errors 0, routing 1.0, argument 1.0, multiturn 1.0.
- Điều đã học: Tool description và schema ảnh hưởng trực tiếp tới argument accuracy, không chỉ việc chọn đúng tool. Khi sửa prompt cần đọc actual tool trace để phân biệt lỗi routing, lỗi tham số và lỗi boundary; không được dùng câu trả lời nghe hợp lý làm bằng chứng duy nhất.
- AI/công cụ đã dùng và cách kiểm tra: Dùng VS Code/Copilot để đọc `chiaviec.md`, registry và các `TOOL.md`, chỉnh artifact bằng patch; dùng evaluator với OpenAI `gpt-4o-mini`; kiểm tra YAML parse, đối chiếu `TOOL_FUNCTIONS`, kiểm tra `provider_error_cases == 0`, `measured_cases == total_cases`, hash artifact và đường dẫn run trong `version_log.csv`.
- Thời điểm đã tự nộp URL repo chung trên VLearn: 01:14 16/09/2026

### Nguyễn Thùy Linh — 2A202602497

- Phần việc và file/commit/PR: Phụ trách Evaluation và version evidence. Chịu trách nhiệm trích xuất, phân tích dữ liệu chạy từ các file run JSON trong `starter_v0/runs/` để xây dựng và duy trì hai artifact bằng chứng chính là `[run-analysis.csv](starter_v0/run-analysis.csv)` và `[version_log.csv](starter_v0/artifacts/version_log.csv)`. Commit riêng cho phần bằng chứng: `33ef289`.
- Quyết định, khó khăn và cách xử lý: Xử lý triệt để xung đột dữ liệu và lệch nhãn version giữa các file run rác và file run OpenAI chuẩn (từ v0 đến v3). Đã dùng script kết hợp PowerShell chuẩn hóa dữ liệu 120 case (30 case/phiên bản), đảm bảo trích xuất chính xác 100% các giá trị `artifact_version`, `prompt_hash`, `tools_hash` và tỉ lệ `metric_after` từ v0 (73.33%) nâng dần lên v3 (100%).
- Điều đã học: Hiểu rõ tầm quan trọng của việc đóng gói dữ liệu minh bạch (traceability) trong phát triển Agent. Nhận diện được các Failure Modes (wrong_tool, wrong_boundary, missing_info) thay đổi ra sao qua từng phiên bản prompt/tool contract.
- AI/công cụ đã dùng và cách kiểm tra: Dùng VS Code Terminal (PowerShell), Python script `parse_runs.py` và `Import-Csv` để kiểm tra gom nhóm dữ liệu (`Group-Object version,passed`); đối chiếu trực tiếp hash và đường dẫn run trong `version_log.csv`.
- Thời điểm đã tự nộp URL repo chung trên VLearn: 03:30 16/09/2026

### Nguyễn Thị Lê Na — 2A202602501

- Phần việc và file/commit/PR: Phụ trách UI và transcript cho agent trong [app.py](starter_v0/app.py). Xây dựng giao diện chat local bằng Streamlit, bổ sung dependency trong [requirements.txt](starter_v0/requirements.txt), và cập nhật hướng dẫn chạy UI trong [README.md](README.md). Commit riêng cho phần UI: `6988f95` (app.py) và `7a9a4bf` (Streamlit dependency).
- Quyết định, khó khăn và cách xử lý: Tái sử dụng trực tiếp `run_model_tool_loop` của CLI thay vì tạo một agent logic riêng, nhờ đó UI giữ nguyên routing, tool contract và safety boundary của evaluator. Sidebar cho phép chọn provider, artifact version, model, history window và số vòng tool; vùng chat hiển thị tin nhắn user/assistant. Mỗi tool event được mở rộng để xem tool name, arguments và result/error. UI cũng thể hiện trạng thái chờ người dùng bổ sung thông tin hoặc xác nhận thông qua `status` do agent loop trả về.
- Transcript và trải nghiệm sử dụng: Mỗi phiên được lưu thành JSON trong [starter_v0/transcripts](starter_v0/transcripts/), chứa artifact version, prompt/tools hash, provider, model, các lượt hội thoại, tool calls và tool results. Có nút reset hội thoại và tải transcript để phục vụ demo, kiểm tra traceability và đối chiếu confirmation boundary. Giao diện được tạo kiểu với nền sáng, màu coral/mint, chat bubble bo tròn và animation nhẹ để dễ theo dõi khi trình bày.
- AI/công cụ đã dùng và cách kiểm tra: Dùng VS Code/Copilot, Streamlit và PowerShell; kiểm tra bằng `py -3 -m py_compile app.py`, diagnostics của VS Code và chạy `py -3 -m streamlit run app.py`. Smoke test endpoint trả về HTTP 200 tại local; kiểm tra UI không thay đổi agent loop và transcript vẫn ghi được tool input/result/error.
- Điều đã học: UI của agent không chỉ cần đẹp mà phải làm rõ bằng chứng thực thi. Việc tách phần hiển thị tool trace khỏi phần chat giúp người dùng phân biệt câu trả lời, dữ liệu tool trả về và lỗi provider; đồng thời tái sử dụng loop giúp tránh chênh lệch giữa UI demo và evaluator.
- Thời điểm đã tự nộp URL repo chung trên VLearn: 8H 16/09/2026

