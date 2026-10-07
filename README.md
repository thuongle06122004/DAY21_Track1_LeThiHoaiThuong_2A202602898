# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Lê Thị Hoài Thương
- MSSV / mã học viên: 2A202602898
- Lớp: H201
- Ngành đã chọn: Giáo dục / AI tutor

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | AI tutor có thể đưa thông tin hoặc hướng dẫn học tập không chính xác, khiến người học tiếp thu kiến thức sai. Khi dùng AI để đánh giá hoặc chuẩn hóa điểm, thiên vị trong dữ liệu và thiết kế có thể làm người học mất cơ hội học tập. Ngoài ra, hệ thống có thể xử lý dữ liệu học tập, hội thoại và dữ liệu của trẻ em. Bên bị ảnh hưởng gồm học sinh/sinh viên, phụ huynh, giáo viên và cơ sở giáo dục. |
| Mức độ high-stakes | Cao. Rủi ro tăng cao khi AI ảnh hưởng đến chấm điểm, xét tuyển, học bổng hoặc khi tương tác với học sinh nhỏ tuổi. Những quyết định này có thể tác động lâu dài đến cơ hội học tập và sức khỏe tinh thần của người học. |
| Dữ liệu nhạy cảm có thể được sử dụng | Dữ liệu định danh như tên, tuổi, trường/lớp; dữ liệu học tập như điểm số, bài làm, lịch sử học; lịch sử hội thoại, dữ liệu hành vi và thông tin sức khỏe tinh thần do người học tự chia sẻ. Bài này không đưa dữ liệu cá nhân thật vào repo. |
| Nhu cầu human review | Cao. Giáo viên cần kiểm tra tính chính xác của nội dung AI và phê duyệt các quyết định đánh giá quan trọng. Nhà trường/chuyên gia phù hợp cần tiếp nhận các tình huống nhạy cảm. Human review cần diễn ra khi thiết lập nguồn học liệu, trước khi dùng kết quả AI cho đánh giá chính thức và khi hệ thống phát hiện dấu hiệu khủng hoảng. |

### 2. Case study 1 — Khanmigo: rủi ro câu trả lời toán học không chính xác của AI tutor

#### Brief Case

- **Tổ chức / sản phẩm AI:** Khan Academy — Khanmigo, công cụ AI hỗ trợ dạy và học.
- **Thời gian, địa điểm / bối cảnh:** Từ năm 2023 tại Hoa Kỳ, trong bối cảnh Khan Academy giới thiệu Khanmigo như một công cụ hỗ trợ giáo viên và người học.
- **AI được dùng để làm gì:** Hỗ trợ học theo hướng gợi mở, đặt câu hỏi và hướng dẫn từng bước thay vì chỉ đưa đáp án ngay cho người học.
- **Vấn đề hoặc sự kiện đáng chú ý:** Một bài báo của *The Wall Street Journal* ghi nhận ví dụ Khanmigo có thể đưa ra hoặc bảo vệ một kết quả toán học không đúng trong quá trình thử nghiệm. Điều này cho thấy AI tutor vẫn có thể trả lời tự tin dù nội dung không chính xác; người học có thể khó phát hiện lỗi nếu thiếu kiểm tra độc lập.
- **Số liệu có nguồn:** *The Wall Street Journal* mô tả **01 ví dụ** phản hồi toán học không đúng trong quá trình thử nghiệm Khanmigo. Đây là số lượng ví dụ được bài báo dùng để minh họa lỗi, không phải nghiên cứu đo tỷ lệ lỗi đại diện cho mọi cuộc hội thoại Khanmigo. Vì nguồn công khai được dùng ở đây không cung cấp tỷ lệ lỗi tổng quát có thể kiểm tra trong bài này, tôi không suy diễn thành phần trăm xác suất lỗi.
- **Nguồn:** [“Khan Academy’s AI Tutor Is Fast, Smart and Sometimes Completely Wrong” — *The Wall Street Journal* — 08/06/2023 — https://www.wsj.com/articles/khan-academy-ai-tutor-khanmigo-test-math-history-c38a3eb5. Thông tin về mục tiêu/sản phẩm: Khan Academy, “Khan Labs / Khanmigo” — https://www.khanacademy.org/khan-labs (truy cập ngày 07/10/2026).](https://www.chalkbeat.org/2026/08/25/ai-tutoring-students-khanmigo-khan-academy-engagement-study/) 
- **Phân biệt bằng chứng và nhận định:** Bằng chứng là bài báo ghi nhận một ví dụ phản hồi toán học không đúng khi thử nghiệm sản phẩm. Nhận định của tôi là phản hồi sai nhưng tự tin có thể tạo over-reliance và gây tác hại học tập. 
#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi học sinh dùng câu trả lời của AI tutor để hoàn thành bài tập hoặc ôn thi mà không đối chiếu sách giáo khoa/giáo viên. |
| Stakeholder bị ảnh hưởng | Trực tiếp: học sinh có thể tiếp thu kiến thức sai. Gián tiếp: giáo viên và phụ huynh phải sửa kiến thức sai; nhà trường và Khan Academy chịu rủi ro mất niềm tin. |
| Failure mode | Hallucination / thông tin không chính xác: AI đưa hướng dẫn hoặc kết quả toán học sai với cách diễn đạt có vẻ thuyết phục. Over-reliance xảy ra nếu người học tin câu trả lời mà không kiểm tra. |
| Layer bắt đầu lỗi | Model hoặc grounding có thể liên quan, nhưng chưa đủ bằng chứng công khai để xác định chính xác layer bắt đầu lỗi. Về mặt kiểm soát, sản phẩm cần cơ chế đối chiếu nguồn và khuyến khích người học kiểm tra lại với giáo viên. |
| Harm xảy ra là gì? | Nguy cơ: học sinh học sai khái niệm, làm sai bài kiểm tra hoặc mất thời gian sửa kiến thức. Nguồn trong bài xác nhận ví dụ phản hồi sai; bài không có đủ bằng chứng để khẳng định hậu quả học tập cụ thể đã xảy ra với một học sinh xác định. |
| Harm lens | Misinformation (thông tin sai) và opportunity loss (nguy cơ giảm cơ hội học tập nếu lỗi được dùng trong đánh giá). |
| Severity | Medium. Tác hại chủ yếu là sai lệch kiến thức và kết quả học tập; mức độ có thể cao hơn nếu lỗi ảnh hưởng đến một kỳ thi hoặc quyết định giáo dục quan trọng. |
| Scale | Chưa đủ dữ liệu để đánh giá quy mô tác động thực tế. Khanmigo là sản phẩm giáo dục có thể tiếp cận nhiều người dùng, nhưng nguồn của case không cho số người bị ảnh hưởng bởi lỗi nêu trên. |
| Probability | Chưa đủ dữ liệu để định lượng. Có bằng chứng về ít nhất một ví dụ lỗi, không đủ để suy ra xác suất trên toàn bộ câu hỏi hoặc toàn bộ người dùng. |
| Frequency | Chưa đủ dữ liệu để đánh giá tần suất. Đây là một ví dụ được nguồn báo chí ghi nhận, không phải thống kê tần suất. |
| Vì sao? | Đánh giá dựa trên bài báo nêu ở Brief Case và giới hạn bằng chứng của bài đó. Vì AI tutor có thể được người học xem là nguồn hướng dẫn đáng tin, human review và kỹ năng kiểm chứng của người học là kiểm soát quan trọng. |

### 3. Case study 2 — Thuật toán chuẩn hóa điểm A-Level của Ofqual tại Anh (2020)

#### Brief Case

- **Tổ chức / sản phẩm AI:** Ofqual (Cơ quan Quản lý Thi cử và Kiểm định chất lượng Anh) — thuật toán chuẩn hóa điểm thi A-Level/GCSE trong đại dịch COVID-19.
- **Thời gian, địa điểm / bối cảnh:** Tháng 08/2020 tại Vương quốc Anh, khi kỳ thi bị hủy do COVID-19 và điểm được chuẩn hóa bằng mô hình sử dụng teacher assessment cùng dữ liệu lịch sử.
- **AI được dùng để làm gì:** Điều chỉnh/chuẩn hóa kết quả đánh giá của giáo viên để cấp điểm A-Level và GCSE trên phạm vi toàn quốc.
- **Vấn đề hoặc sự kiện đáng chú ý:** Thuật toán gây tranh cãi vì có thể hạ kết quả của một số học sinh dựa trên thành tích lịch sử của trường. Sau phản ứng mạnh từ học sinh và công chúng, kết quả do thuật toán chuẩn hóa bị rút lại; điểm teacher assessment được sử dụng thay thế.
- **Số liệu có nguồn:** BBC giải thích rằng 39,1% điểm A-Level dự kiến của giáo viên bị điều chỉnh xuống bởi mô hình chuẩn hóa vào năm 2020. Con số này đo tỷ lệ điểm teacher assessment bị hạ trong đợt chuẩn hóa, không phải số học sinh chắc chắn mất quyền vào đại học.
- **Nguồn:** “A-levels and GCSEs: How did the Ofqual algorithm work and why was it withdrawn?” — BBC News — 20/08/2020 — https://www.bbc.com/news/explainers-53807730.
- **Phân biệt bằng chứng và nhận định:** Bằng chứng là BBC tường thuật mức 39,1% teacher assessment bị hạ và việc rút lại thuật toán. Nhận định của tôi là việc sử dụng thành tích lịch sử của trường có thể tạo bất lợi cho học sinh có năng lực cá nhân cao tại trường có thành tích lịch sử thấp. Tôi không khẳng định mọi học sinh bị hạ điểm đều mất cơ hội đại học vì nguồn không xác nhận điều đó cho từng cá nhân.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi thuật toán chốt điểm A-Level/GCSE dùng cho tốt nghiệp và xét tuyển đại học, thay vì để kết quả đánh giá của giáo viên được giữ nguyên. |
| Stakeholder bị ảnh hưởng | Trực tiếp: học sinh có điểm bị điều chỉnh xuống. Gián tiếp: phụ huynh, giáo viên, trường học, trường đại học và cơ quan quản lý giáo dục. |
| Failure mode | Bias / fairness: mô hình sử dụng dữ liệu lịch sử ở cấp trường có thể không phản ánh chính xác năng lực của từng cá nhân. |
| Layer bắt đầu lỗi | Grounding và model design. Dữ liệu/đặc trưng đầu vào ở cấp trường cùng mục tiêu chuẩn hóa hệ thống có thể tạo kết quả không công bằng cho từng học sinh. Đây là phân tích dựa trên mô tả công khai; không khẳng định chi tiết kỹ thuật ngoài những gì nguồn nêu. |
| Harm xảy ra là gì? | Tác hại đã xảy ra: một phần điểm teacher assessment bị hạ trong đợt chuẩn hóa. Hậu quả có thể gồm lo lắng, mất niềm tin và nguy cơ mất cơ hội học tập đối với người bị ảnh hưởng. Việc mất cơ hội cụ thể của từng học sinh không được suy diễn như một sự kiện đã được nguồn xác nhận. |
| Harm lens | Opportunity loss (mất cơ hội) và dignity loss (cảm giác bị đánh giá không công bằng). |
| Severity | High. Điểm thi là đầu vào quan trọng cho tuyển sinh và có thể ảnh hưởng đáng kể đến lộ trình học tập của học sinh. |
| Scale | High. BBC nêu 39,1% điểm A-Level do giáo viên dự kiến đã bị điều chỉnh xuống trong đợt công bố năm 2020; đây là tác động ở phạm vi hệ thống quốc gia. |
| Probability | Đã xảy ra trong lần vận hành năm 2020 đối với một phần kết quả. Tuy nhiên, không đủ dữ liệu trong nguồn này để tính xác suất tác động cho từng học sinh theo nhóm trường. |
| Frequency | Một sự kiện chuẩn hóa điểm ở quy mô toàn quốc trong bối cảnh kỳ thi năm 2020 bị hủy. Không có căn cứ từ nguồn để gọi đây là lỗi lặp lại thường xuyên qua nhiều kỳ thi. |
| Vì sao? | BBC mô tả tỷ lệ điều chỉnh xuống và việc chính sách bị rút lại. Case cho thấy trong quyết định giáo dục high-stakes, cần human review, cơ chế khiếu nại hiệu quả và đánh giá fairness trước khi triển khai toàn hệ thống. |

### Tự kiểm tra trước khi nộp

- Tôi đã chọn đúng một ngành và phân tích 2 case khác nhau trong ngành Giáo dục / AI tutor.
- Mỗi case có Brief Case, ít nhất một số liệu hoặc bằng chứng có nguồn, URL nguồn và Harm Map đủ 11 trường.
- Tôi đã phân biệt điều nguồn xác nhận với phần nhận định, đồng thời nêu giới hạn khi bằng chứng chưa đủ.
- Tôi không đưa dữ liệu cá nhân thật, hội thoại riêng hoặc thông tin nhạy cảm vào bài.
