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
| Phạm Thị Thùy Linh | 2A202602909 | Liine1310h | Người 1 — Prompt và tool contract: cải thiện system prompt, tool schema, routing, clarification và confirmation boundary | [system_prompt.md](starter_v0/artifacts/system_prompt.md), [tools.yaml](starter_v0/artifacts/tools.yaml), [version_log.csv](starter_v0/artifacts/version_log.csv) |

## Nhận xét chung

- Kết quả và bằng chứng:
- Thay đổi hiệu quả nhất:
- Giới hạn còn lại:
- Cách phân công và tích hợp:

## INDIVIDUAL

Sao chép mục này cho từng thành viên.

### Phạm Thị Thùy Linh — 2A202602909

- Phần việc và file/commit/PR: Phụ trách prompt và tool contract trong [system_prompt.md](starter_v0/artifacts/system_prompt.md) và [tools.yaml](starter_v0/artifacts/tools.yaml). Đã giữ nguyên tên tool, parameter và enum của registry; evidence chạy cùng bộ `data/eval_base.json` được lưu trong [runs](starter_v0/runs/). Commit riêng cho phần artifact: cần ghi hash sau khi commit branch nộp bài.
- Quyết định, khó khăn và cách xử lý: Bổ sung mapping service/device/KB/user/policy/external web; yêu cầu `clarify` khi thiếu ID hoặc environment; buộc chọn đúng `category`, `check`, `response_type`; ngăn employee ID bị dùng như asset ID; và chỉ tạo ticket sau xác nhận `yes_no` hiện tại cho đúng summary, priority và asset ID. Khó khăn chính là model vẫn tự map `demo/QA` sang `staging`, nên thêm rule phủ định rõ cho `demo`, `QA`, `test` và team name. Kết quả cuối đạt 30/30, provider errors 0, routing 1.0, argument 1.0, multiturn 1.0.
- Điều đã học: Tool description và schema ảnh hưởng trực tiếp tới argument accuracy, không chỉ việc chọn đúng tool. Khi sửa prompt cần đọc actual tool trace để phân biệt lỗi routing, lỗi tham số và lỗi boundary; không được dùng câu trả lời nghe hợp lý làm bằng chứng duy nhất.
- AI/công cụ đã dùng và cách kiểm tra: Dùng VS Code/Copilot để đọc `chiaviec.md`, registry và các `TOOL.md`, chỉnh artifact bằng patch; dùng evaluator với OpenAI `gpt-4o-mini`; kiểm tra YAML parse, đối chiếu `TOOL_FUNCTIONS`, kiểm tra `provider_error_cases == 0`, `measured_cases == total_cases`, hash artifact và đường dẫn run trong `version_log.csv`.
- Thời điểm đã tự nộp URL repo chung trên VLearn:
