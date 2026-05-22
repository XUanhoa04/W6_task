# REFLECTIONS

## 2. `idle` vs Trusted Advisor: `idle` uses a 24h CPU window. Trusted Advisor uses 14 days. When do you trust `idle` more, when do you trust TA more?
Cá nhân e  thấy lệnh `idle` (với cửa sổ 24h) cực kỳ phù hợp khi làm các task R&D, test linh tinh. ví dụ hay quên tắt máy sau khi làm xong, nên quét một ngày là ra ngay để đỡ tốn tiền oan. 
Còn với các hệ thống trên production, em  chọn Trusted Advisor. Nó theo dõi tận 14 ngày nên sẽ tránh được cái bẫy cuối tuần ít truy cập, không bị báo nhầm một server quan trọng là "idle" chỉ vì hôm qua là ngày nghỉ không có traffic.

## 3. `clean --apply` blast radius: If you accidentally ran `clean --tag Environment=dev --apply` in an account shared with another team, what would you have wanted in place to limit damage?
Đúng là lệnh này rất nguy hiểm, xóa lộn của team khác thì toang. Để hạn chế thiệt hại, em sẽ muốn áp dụng IAM Policy giới hạn quyền xóa (Terminate/Delete) theo Resource Tag, ví dụ team mình chỉ được xóa nếu có thêm tag `Owner=Group4`. 
Một cách nữa là thay vì nhảy vào xóa luôn, CLI nên có cơ chế bắt buộc gõ lại tên ID nếu số lượng tài nguyên bị xóa cùng lúc vượt quá một ngưỡng nào đó (ví dụ > 3), tránh kiểu "tiện tay" ấn enter quá đà.
