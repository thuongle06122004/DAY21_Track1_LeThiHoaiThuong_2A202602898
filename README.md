### Lab 21 — Phân tích rủi ro AI qua case study thực tế
Họ và tên: Lê Thị Hoài Thương  
MSSV / mã học viên: 2A202602898
Lớp: H201
Ngành đã chọn: Công nghệ nền bản sao số (Digital Twin Infrastructure)

### 1. Industry Risk Snapshot
## Nội dung	Đánh giá của tôi và lý do
Những tác hại chính có thể xảy ra	
1. Sai lệch mô phỏng & Thao túng vận hành: Sai số trong mô hình AI/IoT làm mô phỏng bản sao số rò rỉ hoặc lệch khỏi hệ thống thực (VD: dự báo sai điểm gãy cơ học, cảnh báo tràn/quá tải sai) dẫn đến hỏng hóc thiết bị, ngưng trệ hạ tầng, hoặc tai nạn lao động.
2. Rò rỉ dữ liệu hạ tầng quan trọng: Bản sao số thu thập telemetry realtime (bản đồ 3D, lưu lượng, sơ đồ mạng lưới, trạng thái vận hành); việc lộ dữ liệu này đe dọa an ninh quốc gia/doanh nghiệp.
3. Thiên vị & Sai lệch dự báo (Algorithmic Bias): Mô hình tối ưu hóa tài nguyên phân bổ sai lệch gây bất bình đẳng dịch vụ công cho cư dân.
Bên bị ảnh hưởng: Kỹ sư vận hành, cư dân/người tiêu dùng sử dụng dịch vụ hạ tầng, doanh nghiệp quản lý và các cơ quan nhà nước.
Mức độ high-stakes	
Cao (Critical/High).
Lý do: Công nghệ bản sao số tích hợp AI tác động trực tiếp vào các hệ thống vật lý thực tế (Cyber-Physical Systems) như năng lượng, giao thông, nhà máy sản xuất, cơ sở hạ tầng đô thị. Sự cố từ AI có thể gây thiệt hại tính mạng con người, tài sản quy mô lớn và gián đoạn an ninh hạ tầng quốc gia.

Dữ liệu nhạy cảm có thể được sử dụng	
1. Dữ liệu hạ tầng trọng yếu (Critical Infrastructure Data): Bản đồ không gian 3D, sơ đồ mạng lưới điện/nước, tham số vận hành thiết bị công nghiệp.


2. Dữ liệu định danh & Hành vi cá nhân (PII & Behavioral Data): Vị trí GPS realtime, camera giám sát mật độ di chuyển, lịch trình sinh hoạt cư dân trong smart city/smart building.

3. Dữ liệu vận hành kinh doanh mật: Năng suất nhà máy, thông số quy trình sản xuất độc quyền.

Nhu cầu human review	
Cao (Human-in-the-loop / Human-on-the-loop).


- Ai kiểm tra: Kỹ sư hệ thống (System Reliability Engineers), Kỹ sư vận hành (Operational Engineers), Chuyên gia an toàn dữ liệu AI.


- Ở bước nào: (1) Kiểm định dữ liệu đầu vào (Data Grounding & Validation); (2) Phê duyệt các hành động tự động có tác động vật lý mạnh (Actuation Decisions); (3) Đánh giá định kỳ độ lệch mô hình (Model Drift).


- Vì sao: Đảm bảo tính giải thích được (Explainability), trách nhiệm giải trình (Accountability) theo nguyên tắc Responsible AI và các quy định an toàn mạng, an toàn hạ tầng Việt Nam.

### 2. Case study 1 — Tai nạn xe tự hành Uber ATG tại Tempe, Arizona (2018)
Brief Case
Tổ chức / sản phẩm AI: Uber Advanced Technologies Group (Uber ATG) — Hệ thống tự lái cho xe Volvo XC90.

Thời gian, địa điểm / bối cảnh: Ngày 18/03/2018 tại Tempe, Arizona, Mỹ. Đêm khuya trên đường công cộng.

AI được dùng để làm gì: Nhận diện vật thể (Object Detection & Classification), dự báo quỹ đạo di chuyển (Trajectory Prediction) và tự động phanh/tránh vật cản.

Vấn đề hoặc sự kiện đáng chú ý: Xe tự lái Uber ở chế độ tự động đã đâm vào người đi bộ qua đường (bà Elaine Herzberg) khiến nạn nhân tử vong. Đây là vụ tai nạn tử vong đầu tiên do xe tự hành gây ra đối với người đi bộ trên đường công cộng.

Số liệu có nguồn:

Xe phát hiện người đi bộ trước va chạm 5.6 giây, nhưng liên tục phân loại sai vật thể (từ vật không xác định -> xe tải -> xe đạp -> vật thể tĩnh) và thay đổi dự báo quỹ đạo.

Phanh khẩn cấp tự động bị Uber vô hiệu hóa để tránh hiện tượng xe phanh giật cục (erratic braking), tạo độ trễ trút trách nhiệm sang con người 1 giây. Người giám sát an toàn ngồi trên xe chỉ nhận cảnh báo 1.2 giây trước khi va chạm và can thiệp phanh 0.2 giây sau va chạm (quá muộn). (Nguồn: Báo cáo NTSB/HAR-19/03).

# Nguồn:
Tên tài liệu: NTSB Collision Between a Self-Driving Car and a Pedestrian, Tempe, Arizona, March 18, 2018 (Accident Report NTSB/HAR-19/03).
Đơn vị/tác giả: Ủy ban An toàn Giao thông Quốc gia Mỹ (National Transportation Safety Board - NTSB).
Ngày công bố: 19/11/2019.
URL: https://www.ntsb.gov/investigations/AccidentReports/Reports/HAR1903.pdf
Phân biệt bằng chứng và nhận định:
Bằng chứng (Nguồn xác nhận): Log hệ thống cho thấy thuật toán re-classification liên tục reset bộ nhớ dự báo quỹ đạo; phanh tự động bị ngắt do thiết kế logic của phần mềm Uber; tài xế ngồi lái bị xao nhãng do xem điện thoại.

Nhận định / Suy luận của học viên: Uber đã chấp nhận rủi ro an toàn để ưu tiên trải nghiệm vận hành êm ái (smooth ride); tổ chức thiếu văn hóa an toàn và quy trình Human-in-the-loop bị tê liệt do giả định con người luôn phản ứng kịp thời trong 1 giây.

Harm Map Worksheet
Trường	Phân tích của tôi
High-risk moment	Khi xe di chuyển tốc độ cao (43 mph) trong đêm, AI phát hiện vật thể không xác định băng qua đường nhưng không xác định đúng bản chất người đi bộ đẩy xe đạp.
Stakeholder bị ảnh hưởng	
Trực tiếp: Nạn nhân Elaine Herzberg (tử vong), tài xế giám sát an toàn trên xe (chịu trách nhiệm hình sự/tâm lý).
Gián tiếp: Uber, ngành công nghiệp xe tự hành, công chúng và cơ quan quản lý giao thông.

Failure mode	Sensor Fusion & Classification Flaw: Thuật toán không thể phân loại đúng vật thể ngoài tập dữ liệu huấn luyện (người qua đường không đúng vạch kẻ đường đẩy xe đạp); Logics Reset: Mỗi lần đổi nhãn phân loại, hệ thống lại xóa lịch sử và tính toán lại quỹ đạo từ đầu.
Layer bắt đầu lỗi	
Safety & Logic Layer kết hợp Grounding Layer.

- Lý do: Model phát hiện điểm ảnh, nhưng Grounding Layer gán nhãn sai/chập chờn. Safety Layer bị can thiệp thô bạo (chủ động tắt tính năng phanh khẩn cấp tự động của Volvo mà không có cơ chế phanh dự phòng mềm).

Harm xảy ra là gì?	Tác hại đã xảy ra (Actual Harm): Thiệt hại tính mạng con người (1 người tử vong); mất niềm tin nghiêm trọng của xã hội vào công nghệ tự hành; dự án Uber ATG bị đình chỉ và bán lại sau đó.
Harm lens	Physical Safety Harm (Tác hại an toàn thể chất) & Institutional/Trust Harm (Tác hại lòng tin công cộng).
Severity	Critical (Cực kỳ nghiêm trọng): Dẫn đến tử vong.
Scale	Vừa và lớn (Medium-Large): Tác động trực tiếp 1 nạn nhân, nhưng tác động gián tiếp làm đóng băng toàn bộ hoạt động thử nghiệm xe tự hành trên toàn thế giới trong nhiều tháng.
Probability	Cao (High) trong điều kiện thử nghiệm thực tế khi không có cơ chế dừng an toàn (Fail-safe) thỏa đáng.
Frequency	Thấp (Low): Sự cố tử vong hiếm gặp trên tổng số km lái thử, nhưng hệ quả mang tính thảm họa.
Vì sao?	Đánh giá dựa trên báo cáo chính thức NTSB/HAR-19/03. Sự cố xảy ra do sự đứt gãy ở cả 3 trụ cột: AI Ethics (coi thường sinh mệnh người đi đường khi tắt phanh tự động), AI Safety (thiếu Fail-safe & Redundancy trong kiến trúc phần mềm), và Responsible AI (trút trách nhiệm vô lý lên tài xế giám sát trong khoảng thời gian phản ứng 1 giây).

### 3. Case study 2 — Sự cố thiên vị phân bổ hạ tầng dịch vụ công của Amazon Prime Free Same-Day Delivery (2016)
Brief Case
Tổ chức / sản phẩm AI: Amazon — Thuật toán tối ưu hóa vùng phủ sóng giao hàng trong ngày (Prime Free Same-Day Delivery).
Thời gian, địa điểm / bối cảnh: Tháng 04/2016, tại các đô thị lớn ở Mỹ (Boston, New York, Chicago, Atlanta, Washington D.C., v.v.).
AI được dùng để làm gì: Tự động hóa phân tích dữ liệu mật độ hội viên Prime, chi phí kho vận và khoảng cách để khoanh vùng (ZIP code) cung cấp dịch vụ giao hàng siêu tốc.
Vấn đề hoặc sự kiện đáng chú ý: Thuật toán AI của Amazon vô tình loại bỏ các khu vực tập trung đông người da đen sinh sống ra khỏi bản đồ dịch vụ Same-Day Delivery, ngay cả khi các khu vực đó nằm ngay trung tâm thành phố và xung quanh đều được bao phủ.
Số liệu có nguồn:
Tại Atlanta, 12 mã ZIP bị loại trừ có tỷ lệ người da đen trung bình là 75%, trong khi các mã ZIP được giao hàng có tỷ lệ người da trắng là 75%.
Tại Boston, khu vực Roxbury (đa số cư dân da đen) hoàn toàn bị bỏ qua, trong khi các khu vực giàu có hơn xung quanh (đa số cư dân da trắng) được phục vụ 100%. (Nguồn: Điều tra độc lập từ Bloomberg News).
Nguồn:
Tên tài liệu: Racial Discrimination in Same-Day Delivery: Amazon’s Free Same-Day Delivery Excludes Black Neighborhoods.
Đơn vị/tác giả: Bloomberg News (David Ingold & Spencer Soper).
Ngày công bố: 21/04/2016.
URL: https://www.bloomberg.com/graphics/2016-amazon-same-day/
Phân biệt bằng chứng và nhận định:

Bằng chứng (Nguồn xác nhận): Phân tích dữ liệu bản đồ phân bố mã ZIP của Bloomberg xác nhận sự lệch pha chủng tộc rõ rệt trong các vùng được chọn phục vụ; Amazon khẳng định thuật toán chỉ tính đến chi phí logistic, mật độ Prime và hạ tầng kho bãi chứ không sử dụng thuộc tính chủng tộc (Race).

Nhận định / Suy luận của học viên: Thuật toán sử dụng các biến thay thế (Proxy variables) như mã ZIP, thu nhập trung bình, lịch sử tiêu dùng — vốn mang tính định kiến lịch sử (Historical bias) — dẫn đến phân biệt đối xử gián tiếp (Disparate Impact).

Harm Map Worksheet
Trường	Phân tích của tôi
High-risk moment	Khi mô hình Machine Learning thực hiện phân vùng kinh doanh (Geofencing) tự động để triển khai hạ tầng dịch vụ dựa trên tối ưu hóa lợi nhuận.
Stakeholder bị ảnh hưởng	
Trực tiếp: Cư dân tại các khu vực thiểu số/da đen bị tước bỏ quyền truy cập dịch vụ bình đẳng.
Gián tiếp: Thương hiệu Amazon, cộng đồng xã hội, cơ quan quản lý phân biệt đối xử.

Failure mode	Algorithmic Bias / Disparate Impact: Thuật toán không chứa biến chủng tộc trực tiếp nhưng bị nhiễm proxy bias từ dữ liệu kinh tế - xã hội lịch sử.
Layer bắt đầu lỗi	
Grounding & Data Layer kết hợp Model Layer.

- Lý do: Dữ liệu đầu vào phản ánh sự bất bình đẳng lịch sử về hạ tầng và thu nhập; Model tối ưu hóa hàm mục tiêu đơn miền (Lợi nhuận/Chi phí) mà bỏ qua tham số công bằng (Fairness constraint).
Harm xảy ra là gì?	Tác hại đã xảy ra (Actual Harm): Bất bình đẳng trong truy cập hạ tầng dịch vụ thương mại; chia rẽ kỹ thuật số (Digital divide); củng cố định kiến phân biệt đối xử kinh tế - xã hội.
Harm lens	Societal & Fairness Harm (Tác hại bất bình đẳng xã hội) & Discriminatory Harm (Tác hại phân biệt đối xử).
Severity	Medium-High (Trung bình - Cao): Không gây thiệt hại mạng người ngay lập tức nhưng gây tổn hại nghiêm trọng về mặt xã hội, dân quyền và uy tín tổ chức.
Scale	Rất lớn (Large): Tác động đến hàng triệu cư dân tại nhiều đại đô thị nước Mỹ.
Probability	Rất cao (Very High) khi triển khai các mô hình tối ưu hóa kinh tế thuần túy mà không kiểm soát thiên vị vị trí địa lý.
Frequency	Thường xuyên (Continuous): Xảy ra liên tục trên mọi truy vấn của người dùng ở khu vực bị loại trừ cho đến khi bị phát hiện và can thiệp thủ công.
Vì sao?	
Đối chiếu Luật AI & Chuẩn mực AI Ethics:
1. Thiếu tính Công bằng (Fairness): AI vô tình tạo ra sự phân biệt đối xử gián tiếp.
2. Thiếu đánh giá tác động xã hội (Algorithmic Impact Assessment): Amazon đã không kiểm thử tác hại phân biệt trước khi tung dịch vụ ra diện rộng.


3. Chiếu theo Luật AI Việt Nam (Khoản về Hệ thống AI rủi ro cao & Nguyên tắc Đạo đức AI): Các hệ thống AI phân bổ tài nguyên/dịch vụ thiết yếu mang tính hạ tầng bắt buộc phải trải qua kiểm toán độ thiên vị (Bias Audit) và tuân thủ nguyên tắc không phân biệt đối xử, đảm bảo tính tiếp cận bình đẳng cho mọi đối tượng.
