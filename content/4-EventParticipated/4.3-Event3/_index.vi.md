---
title: "AWS FCAJ Agent Forge - Deepdive Day 2"
date: 2026-08-04
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Bài thu hoạch “AWS FCAJ Agent Forge - Deepdive Day 2”

### Mục Đích Của Sự Kiện

Sự kiện **AWS First Cloud AI Journey – Agent Forge Deep Dive 2026** tập trung vào chủ đề **Personalization, Evaluation & Optimization**, với nội dung chính xoay quanh **Advanced Amazon Bedrock AgentCore**.

Sự kiện giúp người tham gia:

- Tìm hiểu định hướng phát triển nghề nghiệp dành cho kỹ sư Cloud và AI.
- Hiểu rõ hơn về kiến trúc và các thành phần của AI Agent.
- Tìm hiểu cách sử dụng Memory để xây dựng Agent có khả năng ghi nhớ và cá nhân hóa.
- Khám phá khả năng Observability nhằm theo dõi hoạt động của Agent.
- Tìm hiểu AgentCore Evaluations để đánh giá chất lượng và hiệu quả của Agent.
- Khám phá các thành phần như Registry, Harness, Tools, Payments, Optimization và Policy.
- Trực tiếp thực hành xây dựng và cấu hình AI Agent thông qua phương pháp **Vibe Coding**.

Đặc biệt, phần thực hành được hướng dẫn khá chi tiết bởi diễn giả **Anh Pham – Cloud Consultant, G-AsiaPacific Vietnam**, giúp người tham gia chuyển từ việc tìm hiểu lý thuyết sang trực tiếp xây dựng và thử nghiệm Agent.

---

### Danh Sách Diễn Giả

- **Nghia Tran** – Agentic SA
- **Anh Pham** – Cloud Consultant, G-AsiaPacific Vietnam

Phần trình bày của hai diễn giả có tính bổ trợ cho nhau. Trong đó, **Nghia Tran** tập trung vào định hướng phát triển nghề nghiệp, tư duy xây dựng hệ thống AI và các khái niệm quan trọng của AgentCore. Tiếp đó, **Anh Pham** tập trung vào phần thực hành, hướng dẫn người tham gia từng bước xây dựng và thử nghiệm AI Agent bằng Vibe Coding.

---

### Nội Dung Nổi Bật

### 1. Chia sẻ về định hướng phát triển từ anh Hiếu

#### Chiều sâu và chiều rộng trong sự nghiệp

Một trong những nội dung đáng chú ý trong phần chia sẻ của anh Hiếu là cách nhìn về **chiều sâu (depth)** và **chiều rộng (breadth)** trong quá trình phát triển sự nghiệp của một kỹ sư công nghệ.

Theo diễn giả, một kỹ sư không nhất thiết phải lựa chọn hoàn toàn giữa việc chuyên sâu một lĩnh vực và việc biết nhiều lĩnh vực khác nhau. Thay vào đó, có thể xây dựng lộ trình phát triển theo từng giai đoạn.

- Trong giai đoạn đầu, kỹ sư có thể tập trung xây dựng **chiều sâu chuyên môn** trong một lĩnh vực nhất định.
- Sau đó, tiếp tục mở rộng kiến thức sang việc đưa ứng dụng vào môi trường **Production**.
- Khi đã có nền tảng chuyên môn vững chắc, kỹ sư có thể phát triển thêm **chiều rộng**, chẳng hạn như Networking, Security, Cost Optimization hoặc kiến thức nghiệp vụ chuyên ngành.

Cách tiếp cận này giúp tôi nhận ra rằng một kỹ sư Cloud hoặc AI không chỉ cần biết cách lập trình hay sử dụng một dịch vụ cụ thể mà còn phải hiểu cách các thành phần kết hợp với nhau để tạo thành một hệ thống hoàn chỉnh.

#### Điều kiện cần và điều kiện đủ đối với kỹ sư

Diễn giả cũng đề cập đến sự khác biệt giữa **điều kiện cần** và **điều kiện đủ** đối với một kỹ sư.

**Điều kiện cần** có thể được hỗ trợ bởi các chứng chỉ AWS. Chứng chỉ giúp kỹ sư xây dựng kiến thức nền tảng và chứng minh khả năng tiếp cận các công nghệ Cloud.

Tuy nhiên, **điều kiện đủ** không chỉ nằm ở chứng chỉ mà còn nằm ở năng lực đưa một ứng dụng vào môi trường thực tế.

Một kỹ sư cần có khả năng:

- Thiết kế hệ thống.
- Đưa ứng dụng vào môi trường Production.
- Tối ưu chi phí.
- Đảm bảo bảo mật.
- Thiết lập hệ thống giám sát.
- Theo dõi và xử lý sự cố.
- Đảm bảo khả năng vận hành và mở rộng hệ thống.

Điều này giúp tôi hiểu rõ hơn rằng việc một ứng dụng có thể chạy thành công chưa đồng nghĩa với việc hệ thống đã sẵn sàng cho Production.

#### Kỹ năng mềm và Ownership Mindset

Bên cạnh kỹ năng kỹ thuật, diễn giả nhấn mạnh tầm quan trọng của **kỹ năng mềm** đối với kỹ sư công nghệ.

Một kỹ sư cần có khả năng:

- Giao tiếp hiệu quả với những người không có nền tảng kỹ thuật.
- Làm việc và giao tiếp trong môi trường doanh nghiệp.
- Chủ động tìm hiểu và giải quyết vấn đề.
- Tham gia các cộng đồng công nghệ.
- Chia sẻ và trao đổi kiến thức với những người khác.

Đặc biệt, diễn giả nhấn mạnh **Ownership Mindset** – tư duy chủ động và tinh thần chịu trách nhiệm đối với công việc.

Thay vì chỉ thực hiện đúng những gì được giao, kỹ sư cần chủ động tìm hiểu nguyên nhân của vấn đề, đưa ra giải pháp và theo dõi kết quả đến khi vấn đề được giải quyết.

Đây là một bài học mà tôi nhận thấy có thể áp dụng trực tiếp vào quá trình học tập và làm việc nhóm trong các dự án phần mềm.

#### Tư duy sử dụng AI an toàn và có trách nhiệm

Trong bối cảnh AI đang được sử dụng ngày càng phổ biến, diễn giả cũng đề cập đến tầm quan trọng của **Responsible AI**.

Việc sử dụng AI không nên chỉ tập trung vào việc tạo ra kết quả nhanh hơn mà còn phải xem xét:

- Độ chính xác của thông tin.
- Tính an toàn.
- Bảo mật dữ liệu.
- Quyền riêng tư.
- Những rủi ro khi phụ thuộc vào kết quả do AI tạo ra.
- Trách nhiệm của con người trong việc kiểm tra và sử dụng kết quả.

Qua nội dung này, tôi nhận thấy AI nên được xem là công cụ hỗ trợ con người thay vì hoàn toàn thay thế khả năng suy nghĩ và kiểm tra của con người.

#### Cơ hội và thị trường AI tại Việt Nam

Diễn giả cũng chia sẻ về sự phát triển mạnh của thị trường AI tại Việt Nam.

AI đang mở ra nhiều cơ hội trong các lĩnh vực như:

- Logistics.
- EdTech.
- Healthcare.
- Developer Tools.
- Tài chính.
- Doanh nghiệp.

Bên cạnh việc tự học, diễn giả khuyến khích các kỹ sư trẻ tham gia những cộng đồng công nghệ như **FCAJ** và các cuộc thi **Hackathon** để có cơ hội thực chiến, học hỏi từ những người có kinh nghiệm và biến kiến thức thành sản phẩm thực tế.

---

### 2. Tìm hiểu về Memory trong AI Agent

#### Agent cơ bản và Agent có Memory

Một trong những nội dung quan trọng của chương trình là sự khác biệt giữa **Agent cơ bản** và **Agent có Memory**.

Agent cơ bản thường xử lý từng yêu cầu dựa trên thông tin hiện tại hoặc lịch sử hội thoại trong phạm vi context được cung cấp.

Trong khi đó, Agent có Memory có khả năng lưu giữ những thông tin quan trọng từ các phiên làm việc trước và sử dụng lại những thông tin này khi người dùng quay lại.

Ví dụ, một Agent hỗ trợ mua sắm có thể ghi nhớ:

- Thương hiệu người dùng thường quan tâm.
- Màu sắc yêu thích.
- Kích thước sản phẩm.
- Sở thích của người dùng.
- Những lựa chọn đã thực hiện trong các lần tương tác trước.

Nhờ đó, Agent có thể tạo ra trải nghiệm tương tác mang tính cá nhân hóa cao hơn.

#### Thách thức khi tự xây dựng Memory

Nếu tự xây dựng hệ thống Memory từ đầu, lập trình viên phải giải quyết nhiều vấn đề:

- Thiết kế hệ thống lưu trữ.
- Đồng bộ dữ liệu.
- Trích xuất thông tin quan trọng từ hội thoại.
- Tìm kiếm lại thông tin phù hợp.
- Quản lý context window.
- Kiểm soát số lượng token.
- Tối ưu chi phí.
- Đảm bảo khả năng mở rộng.
- Quản lý và vận hành hệ thống.

Việc xây dựng toàn bộ cơ chế Memory từ đầu vì vậy có thể làm tăng đáng kể độ phức tạp của hệ thống.

#### Amazon Bedrock AgentCore Memory

**Amazon Bedrock AgentCore Memory** cung cấp cơ chế hỗ trợ lưu trữ và truy xuất thông tin cho Agent, giúp giảm bớt phần hạ tầng mà lập trình viên phải tự xây dựng.

Cấu trúc Memory được giới thiệu gồm các thành phần chính.

#### Short-Term Memory – STM

**STM (Short-Term Memory)** lưu trữ những thông tin trong thời gian ngắn, chẳng hạn như:

- Raw chat messages.
- Các sự kiện xảy ra trong phiên làm việc.
- Ngữ cảnh của cuộc hội thoại hiện tại.

#### Memory Extraction Module

Đây là thành phần có nhiệm vụ trích xuất những thông tin quan trọng từ dữ liệu hội thoại.

Thay vì lưu toàn bộ nội dung hội thoại để sử dụng lại, hệ thống có thể xác định những thông tin có giá trị lâu dài.

Ví dụ:

- Người dùng thường chọn một thương hiệu nhất định.
- Người dùng thích một màu cụ thể.
- Người dùng thường sử dụng một kích thước sản phẩm nhất định.

#### Long-Term Memory – LTM

**LTM (Long-Term Memory)** lưu giữ những thông tin đã được trích xuất để Agent có thể sử dụng trong những lần tương tác sau.

Các thông tin này có thể được biểu diễn dưới dạng vector, giúp Agent tìm kiếm và truy xuất những thông tin liên quan khi người dùng quay lại sau một khoảng thời gian dài.

Qua phần này, tôi hiểu rõ hơn rằng Memory không đơn giản chỉ là việc lưu lại toàn bộ lịch sử trò chuyện mà còn bao gồm quá trình **trích xuất, lưu trữ và truy xuất những thông tin có giá trị đối với Agent**.

---

### 3. AgentCore Observability

Một nội dung quan trọng khác được giới thiệu là **AgentCore Observability**.

Đối với một AI Agent, việc chỉ biết câu trả lời cuối cùng là chưa đủ. Trong quá trình vận hành, người phát triển cần biết Agent đã thực hiện những bước nào, sử dụng công cụ nào và trạng thái xử lý ra sao.

AgentCore cung cấp cơ chế theo dõi hoạt động của Agent thông qua:

- Logs.
- Traces.
- Tool invocation.
- Trạng thái xử lý.
- Các bước trong quá trình Agent thực hiện nhiệm vụ.

Cách quản lý này có nhiều điểm tương đồng với cách sử dụng **Amazon CloudWatch** để theo dõi các hệ thống AWS truyền thống.

Observability đặc biệt quan trọng khi đưa AI Agent vào Production.

Ví dụ, nếu Agent đưa ra một kết quả không chính xác, hệ thống Observability có thể giúp người phát triển tìm hiểu:

1. Agent nhận input như thế nào.
2. Agent đã lựa chọn Tool nào.
3. Tool có trả về dữ liệu chính xác hay không.
4. Quá trình xử lý có xảy ra lỗi hay không.
5. Output cuối cùng được hình thành như thế nào.

Qua đó, việc Debug và cải thiện Agent trở nên dễ dàng hơn.

---

### 4. Đánh giá chất lượng Agent với AgentCore Evaluations

Một AI Agent cần được đánh giá thường xuyên để xác định chất lượng hoạt động.

**AgentCore Evaluations** hỗ trợ việc đo lường và đánh giá hiệu quả của Agent dựa trên những tiêu chí được thiết lập.

Một phương pháp được giới thiệu là **LLM-as-a-Judge**, trong đó một mô hình ngôn ngữ khác có thể đóng vai trò như một "giám khảo" để đánh giá output của Agent.

Các tiêu chí đánh giá có thể bao gồm:

- Độ chính xác.
- Mức độ phù hợp với yêu cầu.
- Chất lượng câu trả lời.
- Mức độ tuân thủ quy tắc.
- Khả năng hoàn thành nhiệm vụ.

Điều này giúp quá trình phát triển Agent có thể thực hiện theo một vòng lặp:

**Đo lường → Phát hiện vấn đề → Cải thiện → Đánh giá lại**

Thay vì chỉ dựa vào cảm nhận của người phát triển, chất lượng Agent có thể được đánh giá dựa trên các tiêu chí cụ thể hơn.

---

### 5. Các thành phần chính của AgentCore

Phần trình bày giới thiệu nhiều thành phần hỗ trợ quá trình xây dựng và vận hành AI Agent.

Các chức năng nổi bật gồm:

- **Memory:** quản lý thông tin và ngữ cảnh dài hạn của Agent.
- **Observability:** giám sát và theo dõi hoạt động của Agent.
- **Evaluations:** đánh giá chất lượng Agent.
- **Tools:** cho phép Agent tương tác với các công cụ và hệ thống bên ngoài.
- **Session Management:** quản lý phiên làm việc.
- **Runtime Execution:** cung cấp môi trường thực thi cho Agent.

Ngoài ra, chương trình còn giới thiệu các thành phần như:

- Registry.
- Harness.
- Payments.
- Optimization.
- Policy.

Qua đó, tôi nhận thấy một hệ thống AI Agent hoàn chỉnh không chỉ bao gồm một mô hình LLM mà còn cần nhiều thành phần hỗ trợ xung quanh để có thể hoạt động ổn định và an toàn.

### Các thành phần cơ bản khi thiết lập Agent

Việc xây dựng Agent có thể tập trung vào ba thành phần chính:

#### LLM Model

Lựa chọn mô hình nền tảng phù hợp với yêu cầu về:

- Khả năng xử lý.
- Tốc độ phản hồi.
- Chi phí.
- Mục đích sử dụng.

#### System Prompt

System Prompt định hình:

- Vai trò của Agent.
- Nhiệm vụ.
- Cách thức phản hồi.
- Các quy tắc.
- Những giới hạn mà Agent cần tuân thủ.

#### Tools & Skills

Tools & Skills cung cấp cho Agent khả năng thực hiện các tác vụ bên ngoài việc sinh văn bản.

Ví dụ:

- Gọi API.
- Truy vấn dữ liệu.
- Thực hiện hành động trên hệ thống.
- Sử dụng các công cụ bên ngoài.

---

### 6. Phần thực hành – Hands-on Lab

#### Hướng dẫn thực hành từ Anh Pham

Sau phần trình bày lý thuyết, chương trình chuyển sang phần **Hands-on Lab** do anh **Anh Pham – Cloud Consultant, G-AsiaPacific Vietnam** trực tiếp hướng dẫn.

Đây là phần tôi đánh giá rất cao trong chương trình vì nội dung không chỉ dừng lại ở việc giới thiệu khái niệm mà diễn giả hướng dẫn **rất chi tiết từng bước thực hành**.

Phần thực hành sử dụng phương pháp **Vibe Coding**, trong đó AI được sử dụng như một trợ lý hỗ trợ quá trình phát triển.

Thay vì phải tự viết toàn bộ mã nguồn từ đầu, người phát triển có thể mô tả yêu cầu bằng ngôn ngữ tự nhiên và sử dụng AI để hỗ trợ:

- Tạo cấu trúc ban đầu.
- Sinh mã nguồn.
- Giải thích code.
- Phát hiện lỗi.
- Sửa lỗi.
- Điều chỉnh chức năng.
- Thử nghiệm các cách triển khai khác nhau.

Qua phần thực hành, tôi nhận thấy Vibe Coding có thể giúp rút ngắn đáng kể thời gian từ lúc hình thành ý tưởng đến khi có một Prototype có thể chạy được.

#### Thực hành xây dựng Agent

Diễn giả hướng dẫn từng bước để người tham gia có thể bắt đầu xây dựng một AI Agent.

Quá trình thực hành giúp người tham gia hiểu rõ hơn mối quan hệ giữa:

**LLM Model → System Prompt → Tools & Skills → Agent Runtime**

Thay vì chỉ xem một Demo đã được chuẩn bị sẵn, người tham gia có thể theo dõi quá trình xây dựng và cấu hình Agent.

Điều này giúp các khái niệm được trình bày trong phần lý thuyết trở nên trực quan và dễ hiểu hơn.

#### Thực hành thêm Memory

Một trong những nội dung thực hành là bổ sung **Memory** cho Agent.

Qua đó có thể quan sát sự khác biệt giữa:

- Agent chỉ xử lý yêu cầu hiện tại.
- Agent có khả năng ghi nhớ thông tin của người dùng.
- Agent có thể sử dụng lại thông tin đã ghi nhớ trong những lần tương tác tiếp theo.

Phần thực hành này giúp tôi hiểu rõ hơn về ý nghĩa của STM, Memory Extraction và LTM được trình bày ở phần lý thuyết.

#### Thực hành Agent Observability

Diễn giả tiếp tục hướng dẫn cách khám phá **Agent Observability**.

Thay vì chỉ nhìn vào câu trả lời cuối cùng, người tham gia có thể quan sát quá trình Agent xử lý yêu cầu.

Qua đó có thể hiểu rõ hơn:

- Agent thực hiện những bước nào.
- Agent gọi Tool nào.
- Trạng thái xử lý ra sao.
- Những thông tin nào có thể được sử dụng để Debug.

Điều này giúp tôi nhận thấy Observability là một thành phần rất quan trọng nếu muốn đưa AI Agent vào môi trường Production.

#### Thực hành AgentCore Evaluations

Phần tiếp theo là trải nghiệm với **AgentCore Evaluations**.

Người tham gia được tìm hiểu cách đánh giá chất lượng của Agent thay vì chỉ kiểm tra kết quả bằng cách quan sát thủ công.

Đây là một điểm quan trọng bởi AI có tính biến động. Một Agent có thể cho kết quả tốt trong một số trường hợp nhưng không đảm bảo luôn hoạt động chính xác trong mọi tình huống.

Việc xây dựng cơ chế Evaluation giúp quá trình cải tiến Agent có cơ sở rõ ràng hơn.

#### Khám phá AgentCore Harness

Phần thực hành cũng giới thiệu và hướng dẫn khám phá **AgentCore Harness**.

Thông qua cách hướng dẫn trực tiếp, người tham gia có thể hình dung rõ hơn cách các thành phần hỗ trợ Agent được kết hợp trong quá trình xây dựng một hệ thống hoàn chỉnh.

Điểm tôi đánh giá cao nhất ở phần Hands-on là diễn giả **Anh Pham hướng dẫn rất chi tiết và theo sát quá trình thực hành**, từ việc bắt đầu xây dựng Agent, cấu hình các thành phần, sử dụng Vibe Coding cho đến kiểm tra kết quả.

Điều này đặc biệt hữu ích đối với những người mới tiếp cận AgentCore vì có thể vừa nghe giải thích, vừa thực hiện theo từng bước thay vì chỉ tiếp nhận kiến thức ở mức lý thuyết.

---

### Những Gì Học Được

#### Về tư duy phát triển nghề nghiệp

- Hiểu được sự cân bằng giữa **chiều sâu và chiều rộng** trong quá trình phát triển của một kỹ sư.
- Nhận ra rằng chứng chỉ chỉ là nền tảng, còn năng lực triển khai và vận hành hệ thống thực tế mới là yếu tố quan trọng.
- Hiểu được tầm quan trọng của Production, Security, Cost Optimization và Observability.
- Nhận thức rõ hơn về **Ownership Mindset** và tính chủ động trong công việc.
- Hiểu rằng kỹ năng giao tiếp và khả năng làm việc với những người không chuyên về kỹ thuật cũng rất quan trọng.

#### Về AI Agent

- Hiểu rõ hơn về kiến trúc của một AI Agent.
- Hiểu sự khác biệt giữa Agent có Memory và Agent cơ bản.
- Hiểu cách STM và LTM hỗ trợ quá trình ghi nhớ.
- Biết được vai trò của Memory Extraction trong việc trích xuất thông tin quan trọng.
- Hiểu vai trò của Tools và Skills trong việc mở rộng khả năng của Agent.
- Nhận thức được tầm quan trọng của Session Management và Runtime Execution.

#### Về Observability và Evaluation

- Hiểu rằng AI Agent cần được giám sát tương tự như các hệ thống phần mềm truyền thống.
- Biết được vai trò của Logs và Traces trong quá trình Debug Agent.
- Hiểu cách Observability giúp theo dõi Tool Invocation và trạng thái hoạt động của Agent.
- Hiểu khái niệm **LLM-as-a-Judge** trong việc đánh giá output.
- Nhận thức được việc đánh giá Agent cần được thực hiện liên tục trong quá trình phát triển.

#### Về Vibe Coding

Phần thực hành giúp tôi có thêm trải nghiệm về **Vibe Coding** và cách sử dụng AI như một trợ lý trong quá trình phát triển phần mềm.

Tôi nhận thấy Vibe Coding có thể:

- Tăng tốc quá trình tạo Prototype.
- Hỗ trợ viết code nhanh hơn.
- Hỗ trợ Debug.
- Giúp thử nghiệm nhiều ý tưởng trong thời gian ngắn.
- Giảm thời gian thực hiện những công việc lập trình lặp lại.

Tuy nhiên, người lập trình vẫn cần hiểu kiến thức nền tảng để kiểm tra, đánh giá và chịu trách nhiệm đối với kết quả do AI tạo ra.

---

### Ứng Dụng Vào Công Việc

Những kiến thức từ sự kiện có thể được áp dụng vào các dự án Cloud và AI trong tương lai.

#### Đối với phát triển phần mềm

- Sử dụng AI để hỗ trợ quá trình lập trình.
- Tận dụng Vibe Coding để nhanh chóng xây dựng Prototype.
- Sử dụng AI để hỗ trợ Debug và phân tích lỗi.
- Kiểm tra lại code và kết quả do AI tạo ra trước khi sử dụng.

#### Đối với hệ thống Cloud

- Quan tâm đến khả năng vận hành Production ngay từ giai đoạn thiết kế.
- Thiết kế hệ thống có Logging và Observability.
- Quan tâm đến Security.
- Tối ưu chi phí sử dụng Cloud.
- Thiết kế hệ thống có khả năng mở rộng.

#### Đối với AI Agent

Trong những dự án tương lai, tôi có thể áp dụng:

- **Memory** để cá nhân hóa Agent.
- **Tools** để Agent tương tác với hệ thống bên ngoài.
- **Observability** để theo dõi hoạt động.
- **Evaluations** để đo lường chất lượng.
- **Policy** để kiểm soát hành vi của Agent.
- **Vibe Coding** để tăng tốc quá trình phát triển Prototype.

---

### Trải Nghiệm Trong Event

Tham gia sự kiện **AWS First Cloud AI Journey – Agent Forge Deep Dive 2026** đã giúp tôi có cái nhìn rõ hơn về xu hướng phát triển của AI Agent và cách xây dựng một hệ thống Agent theo hướng thực tế.

#### Học hỏi từ các chuyên gia

Phần chia sẻ của **Nghia Tran** giúp tôi có thêm góc nhìn về định hướng phát triển của một kỹ sư trong thời đại AI.

Những nội dung về **chiều sâu, chiều rộng, Production, Responsible AI và Ownership Mindset** giúp tôi hiểu rằng một kỹ sư cần phát triển cả kỹ năng chuyên môn lẫn kỹ năng mềm.

#### Hiểu thêm về Amazon Bedrock AgentCore

Qua phần lý thuyết, tôi hiểu rõ hơn về các thành phần cần thiết để xây dựng một AI Agent hoàn chỉnh.

Đặc biệt, tôi có thêm kiến thức về:

- Memory.
- Observability.
- Evaluations.
- Tools.
- Session Management.
- Runtime Execution.
- Harness.
- Policy.
- Optimization.

#### Trải nghiệm Hands-on

Phần thực hành do **Anh Pham** hướng dẫn là phần tôi cảm thấy hữu ích nhất.

Diễn giả không chỉ giới thiệu các tính năng mà còn **hướng dẫn rất chi tiết từng bước**, giúp người tham gia có thể theo dõi và thực hành cùng lúc.

Việc sử dụng **Vibe Coding** trong quá trình thực hành cũng giúp tôi hình dung rõ hơn cách AI có thể trở thành một trợ lý lập trình, hỗ trợ từ việc xây dựng cấu trúc, viết code, sửa lỗi cho đến thử nghiệm các chức năng.

Đặc biệt, việc trực tiếp trải nghiệm Memory, Observability, Evaluations và Harness giúp tôi hiểu rõ hơn mối liên hệ giữa các thành phần này trong một hệ thống Agent thực tế.

---

### Bài Học Rút Ra

Qua sự kiện, tôi rút ra một số bài học quan trọng:

- Công nghệ AI đang phát triển rất nhanh, vì vậy khả năng học hỏi và thích ứng là yếu tố quan trọng đối với kỹ sư phần mềm.
- Một kỹ sư không chỉ cần biết cách xây dựng ứng dụng mà còn phải hiểu cách đưa ứng dụng vào môi trường Production.
- Chứng chỉ AWS là nền tảng tốt nhưng cần kết hợp với kinh nghiệm thực tế.
- AI Agent không chỉ là một LLM kết hợp với Prompt mà cần nhiều thành phần hỗ trợ như Memory, Tools, Runtime, Observability và Evaluation.
- Memory giúp Agent có khả năng cá nhân hóa trải nghiệm người dùng.
- Observability và Evaluation là những thành phần quan trọng khi đưa Agent vào môi trường thực tế.
- Vibe Coding có thể giúp tăng tốc quá trình phát triển nhưng không loại bỏ vai trò của người lập trình.
- AI cần được sử dụng một cách có trách nhiệm, đặc biệt khi làm việc với dữ liệu và các hệ thống thực tế.
- Tham gia cộng đồng và các cuộc thi công nghệ là một cách hiệu quả để chuyển kiến thức lý thuyết thành kinh nghiệm thực tế.

---

### Kết Luận

Sự kiện **AWS First Cloud AI Journey – Agent Forge Deep Dive 2026** đã giúp tôi mở rộng kiến thức về **Agentic AI và Amazon Bedrock AgentCore**, đặc biệt là các khía cạnh quan trọng khi xây dựng AI Agent theo hướng thực tế như **Memory, Observability và Evaluation**.

Nếu phần lý thuyết giúp tôi hiểu **Agent cần những thành phần nào và tại sao chúng quan trọng**, thì phần Hands-on do **Anh Pham** hướng dẫn giúp tôi hiểu rõ hơn **cách bắt đầu xây dựng và kiểm thử một Agent trong thực tế**.

Tôi đặc biệt ấn tượng với cách diễn giả hướng dẫn thực hành chi tiết bằng **Vibe Coding**. Việc kết hợp giữa AI và lập trình giúp rút ngắn thời gian xây dựng Prototype, đồng thời tạo điều kiện để người học nhanh chóng thử nghiệm các ý tưởng mới.

Qua sự kiện, tôi nhận thức rõ hơn rằng việc xây dựng AI Agent không chỉ là lựa chọn một mô hình AI mạnh mà còn là quá trình kết hợp giữa **AI, Cloud Computing, Software Engineering, Security, Observability và tư duy vận hành Production**.

Đây là những kiến thức có giá trị đối với quá trình học tập cũng như định hướng phát triển của tôi trong lĩnh vực **Cloud Computing, AI và Software Engineering** trong thời gian tới.

---

### Một Số Hình Ảnh Khi Tham Gia Sự Kiện

_Chèn hình ảnh banner sự kiện và các hình ảnh trong quá trình tham gia Hands-on Lab tại đây._

![AWS First Cloud AI Journey – Agent Forge Deep Dive 2026](../../images/agent-forge.png)
