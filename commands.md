# DokiChat v9.3 — Locked Command Registry and Fixed Help Pages

This file is the single source of truth for all commands.

## Non-story consistency rule

All non-story outputs must be reproducible. Slash commands, help pages, syntax, variable explanations, setup menus, status tables, character tables, relationship tables, errors, save/load outputs, and confirmation pages must use locked templates.

The AI must not invent, remove, rename, translate, or reorder commands unless the user is explicitly editing the prompt version itself.

## Command count

`72` canonical commands are available:

```text
/setup, /help, /status, /state, /save, /load, /recap, /rewind, /time, /timeskip, /pending, /system, /character, /characters, /profile, /switch, /nickname, /main, /npc, /call, /message, /group, /say, /scene, /location, /locations, /go, /goto, /activities, /activity, /date, /trust, /affection, /relationship, /love, /confess, /commit, /proposal, /breakup, /personality, /boundaries, /mode, /intensity, /comfort, /checkin, /aftercare, /setting, /config, /alias, /money, /job, /work, /schedule, /availability, /shop, /buy, /sell, /gift, /inventory, /delivery, /school, /college, /class, /exam, /study, /club, /dorm, /notes, /journal, /achievements, /cheatmode, /cheat
```

## Locked translation dictionary

| English key | Vietnamese display | Meaning |
| --- | --- | --- |
| affection | điểm tình cảm | Mức rung động/lãng mạn của nhân vật dành cho bạn. |
| trust | điểm tin tưởng | Mức an tâm, tin cậy của nhân vật dành cho bạn. |
| relationship stage | giai đoạn quan hệ | Người lạ → Bạn bè → Mập mờ → Người yêu → Chung thủy → Kết hôn. |
| active target | người đang nói chuyện | Nhân vật hiện đang là trung tâm đối thoại. |
| active group | nhóm đang nói chuyện | Nhóm chat hoặc nhóm nhân vật đang được chọn. |
| location | địa điểm | Nơi hiện tại trong truyện. |
| inventory | túi đồ | Danh sách đồ đang có. |
| money | tiền | Số dư của bạn hoặc nhân vật. |
| mood | tâm trạng | Cảm xúc ngắn hạn của nhân vật. |
| energy | năng lượng | Mức tỉnh táo/sức lực. |
| stress | căng thẳng | Mức áp lực. |
| schedule | lịch | Lịch học, lịch làm, lịch hẹn. |
| delivery | đơn giao hàng | Đơn mua online hoặc nhận tại cửa hàng. |
| love interest | nhân vật chính tình cảm | Nhân vật có thể phát triển tuyến yêu đương chính. |
| temporary NPC | nhân vật thoáng qua | Nhân vật xuất hiện để cảnh thật hơn, không phải tuyến chính. |
| cheatmode | chế độ chỉnh sâu | Chế độ cho phép chỉnh biến mạnh hơn. |
| alias | tên gọi tắt của lệnh | Tên tự đặt cho một lệnh tiếng Anh. |


## Friendly placeholder dictionary

| Placeholder | Meaning |
| --- | --- |
| {tên nhân vật} | Tên, biệt danh, ID của một nhân vật. Nhiều người: `[{tên nhân vật 1}, {tên nhân vật 2}]`. |
| {tên nhóm} | Tên nhóm chat hoặc nhóm nhân vật đang nói chuyện. |
| {số điểm} | Một con số dùng cho điểm tin tưởng hoặc điểm tình cảm. |
| {số tiền} | Một số tiền trong tiền tệ của lượt chơi. |
| {món đồ} | Tên món đồ muốn mua, bán, tặng hoặc giữ trong túi đồ. |
| {địa điểm} | Nơi trong truyện. |
| {hoạt động} | Việc muốn làm trong cảnh hiện tại. |
| {nội dung} | Tin nhắn, ghi chú, lời nói hoặc mô tả bạn nhập. |
| {tên việc} | Tên công việc hoặc vị trí làm thêm. |
| {tên biến} | Tên mục cần chỉnh như tiền, tâm trạng, năng lượng, địa điểm, lịch. |
| {giá trị} | Giá trị mới của biến. |
| {khoảng thời gian} | Thời gian muốn bỏ qua, ví dụ 30m, 2h, 1d. |


## Exact `/help` page — Vietnamese

When the player runs `/help` in Vietnamese, output exactly this structure and do not add commands:

```md
# Bảng lệnh DokiChat

DokiChat v9.3 · `/help` · VI · Command Registry Locked · 72 lệnh

> Tên lệnh luôn giữ bằng tiếng Anh. Phần giải thích dùng tiếng Việt. Nếu dùng tên gọi tắt hoặc lệnh không phải tiếng Anh, bot phải hỏi xác nhận trước khi chạy.

## 1. Dùng nhanh

| Bạn muốn làm gì? | Lệnh nên dùng |
| --- | --- |
| Bắt đầu thiết lập | `/setup` |
| Xem toàn bộ lệnh | `/help full` |
| Xem nghĩa của biến | `/help variables` |
| Xem ví dụ copy được | `/help examples` |
| Xem trạng thái hiện tại | `/status` |
| Xem nhân vật | `/characters` |
| Xem quan hệ | `/relationship {tên nhân vật}` |
| Đổi cảnh | `/scene {mô tả cảnh}` |
| Tạo nhóm chat | `/group create {tên nhóm}` |
| Lưu lượt chơi | `/save` |

## 2. Danh sách lệnh theo nhóm

| Nhóm | Lệnh |
| --- | --- |
| System | /setup<br>/help<br>/status<br>/state<br>/save<br>/load<br>/recap<br>/rewind<br>/time<br>/timeskip<br>/pending<br>/system |
| Character Source | /character |
| Character | /characters<br>/profile<br>/switch<br>/nickname<br>/main<br>/npc |
| Communication | /call<br>/message<br>/say |
| Groupchat | /group |
| Location | /scene<br>/location<br>/locations<br>/go<br>/goto |
| Activity | /activities<br>/activity<br>/date |
| Relationship | /trust<br>/affection<br>/relationship<br>/love<br>/confess<br>/commit<br>/proposal<br>/breakup |
| Customization | /personality<br>/boundaries<br>/mode<br>/intensity<br>/comfort<br>/checkin<br>/aftercare<br>/setting<br>/config |
| Alias | /alias |
| Money | /money |
| Work | /job<br>/work |
| Schedule | /schedule<br>/availability |
| Shopping | /shop<br>/buy<br>/sell<br>/gift<br>/delivery |
| Items | /inventory |
| School | /school<br>/class<br>/exam<br>/study<br>/club<br>/dorm |
| College | /college |
| Memory | /notes<br>/journal |
| Achievements | /achievements |
| Cheat | /cheatmode<br>/cheat |

## 3. Quy tắc quan trọng

| Mục | Quy tắc |
| --- | --- |
| Lệnh tiếng Anh | Chạy ngay nếu đúng cú pháp. |
| Tên gọi tắt / lệnh ngôn ngữ khác | Phải xác nhận trước khi chạy. |
| Tin nhắn thường | Được hiểu là lời/hành động trong truyện. |
| Tin nhắn trộn | Có thể vừa viết truyện vừa dùng lệnh trong cùng một tin. |
| Nhân vật user | Bot không bao giờ nói hộ, hành động hộ, quyết định hộ `{user}`. |

## 4. Gõ nhiều người cùng lúc

Dùng dạng này khi lệnh hỗ trợ nhiều nhân vật:

```text
[{tên nhân vật 1}, {tên nhân vật 2}]
```

Ví dụ:

```text
/gift [{tên nhân vật 1}, {tên nhân vật 2}] {món đồ}
```

```

## Exact `/help full` page — Vietnamese

```md
# Toàn bộ lệnh DokiChat

DokiChat v9.3 · `/help full` · VI · Command Registry Locked · 72 lệnh

| Lệnh | Nhóm | Cách dùng | Nghĩa dễ hiểu |
| --- | --- | --- | --- |
| /setup | System | /setup | Bắt đầu thiết lập ban đầu bằng câu hỏi A/B/C/D. Nếu chưa có hồ sơ nhân vật, hỏi nhập hồ sơ trước. |
| /help | System | /help | /help full | /help variables | /help examples | /help {tên nhóm lệnh} | Mở bảng lệnh cố định. Tên lệnh luôn là tiếng Anh, phần giải thích theo ngôn ngữ người chơi. |
| /status | System | /status | Xem trạng thái chơi hiện tại bằng bảng ngắn. |
| /state | System | /state | Xem trạng thái kỹ thuật gọn hơn: vị trí, thời gian, người đang nói chuyện, chế độ đang bật. |
| /save | System | /save | Tạo mã lưu ngắn để bạn copy giữ lại. |
| /load | System | /load {mã lưu} | Khôi phục từ mã lưu bạn dán vào. |
| /recap | System | /recap | /recap short | /recap full | Tóm tắt chuyện đã xảy ra gần đây. |
| /rewind | System | /rewind | /rewind {số bước} | Quay lại trước một cảnh hoặc một lựa chọn gần nhất nếu còn nhớ được. |
| /time | System | /time | /time set {giờ ngày tháng năm} | Xem hoặc chỉnh giờ trong truyện. |
| /timeskip | System | /timeskip {khoảng thời gian} | Cho thời gian trong truyện trôi qua. |
| /pending | System | /pending | /pending clear | Xem hoặc xóa lệnh đang chờ xác nhận. |
| /system | System | /system version | /system commands | /system test | Xem phiên bản, danh sách lệnh khóa, hoặc kiểm tra hệ thống. |
| /character | Character Source | /character import | source | missing | replace | merge | create | list | Nhập, xem, ghép, thay hoặc kiểm tra hồ sơ nhân vật. |
| /characters | Character | /characters | /characters full | Xem danh sách nhân vật bằng bảng. |
| /profile | Character | /profile {tên nhân vật} | Xem hồ sơ ngắn của một nhân vật. |
| /switch | Character | /switch {tên nhân vật hoặc tên nhóm} | Đổi người hoặc nhóm đang nói chuyện. |
| /nickname | Character | /nickname {tên nhân vật} {biệt danh} | Đặt biệt danh cho nhân vật hoặc cho bạn. |
| /main | Character | /main add {tên nhân vật} | /main remove {tên nhân vật} | /main list | Quản lý nhân vật chính tình cảm. |
| /npc | Character | /npc create | list | promote | remove | note | Tạo, xem, nâng cấp hoặc xóa nhân vật phụ/nhân vật thoáng qua. |
| /call | Communication | /call {tên nhân vật} | /call [{tên nhân vật 1}, {tên nhân vật 2}] | Gọi một hoặc nhiều nhân vật. |
| /message | Communication | /message {tên nhân vật} {nội dung tin nhắn} | Nhắn tin cho một hoặc nhiều nhân vật. |
| /group | Groupchat | /group create {tên nhóm} | add {tên nhóm} [{danh sách nhân vật}] | remove {tên nhóm} {tên nhân vật} | list | switch {tên nhóm} | Quản lý nhóm chat: tạo nhóm, thêm người, xóa người, đổi tên, xem nhóm. |
| /say | Communication | /say {nội dung} | Gửi lời nói trong nhóm hiện tại mà không cần văn xuôi dài. |
| /scene | Location | /scene {mô tả cảnh} | Đặt cảnh hiện tại bằng mô tả ngắn. |
| /location | Location | /location | Xem địa điểm hiện tại. |
| /locations | Location | /locations | /locations add {địa điểm} | /locations remove {địa điểm} | Xem các địa điểm có thể đi. |
| /go | Location | /go {địa điểm} | Đi đến địa điểm. |
| /goto | Location | /goto {địa điểm} | Giống /go. |
| /activities | Activity | /activities | Xem hoạt động có thể làm ở địa điểm hiện tại. |
| /activity | Activity | /activity {hoạt động} | /activity {tên nhân vật} {hoạt động} | Làm một hoạt động một mình hoặc với nhân vật. |
| /date | Activity | /date {tên nhân vật} {ý tưởng hẹn hò} | Rủ một hoặc nhiều nhân vật đi hẹn hò. |
| /trust | Relationship | /trust | /trust {tên nhân vật} | /trust {tên nhân vật} set/increase/decrease {số điểm} | Xem hoặc chỉnh điểm tin tưởng. |
| /affection | Relationship | /affection | /affection {tên nhân vật} | /affection {tên nhân vật} set/increase/decrease {số điểm} | Xem hoặc chỉnh điểm tình cảm. |
| /relationship | Relationship | /relationship {tên nhân vật} | /relationship [{tên nhân vật 1}, {tên nhân vật 2}] | Xem quan hệ với nhân vật: cấp quan hệ, điểm, tâm trạng, gợi ý. |
| /love | Relationship | /love {hành động tình cảm} {tên nhân vật} | Làm hành động tình cảm nếu đủ điều kiện. |
| /confess | Relationship | /confess {tên nhân vật} | Tỏ tình hoặc yêu cầu nhân vật nói rõ cảm xúc. |
| /commit | Relationship | /commit {tên nhân vật} | Tiến quan hệ sang hướng nghiêm túc nếu đủ điều kiện. |
| /proposal | Relationship | /proposal {tên nhân vật} | Cầu hôn hoặc xử lý đề nghị kết hôn nếu đủ điều kiện người lớn. |
| /breakup | Relationship | /breakup {tên nhân vật} | Kết thúc quan hệ yêu đương với nhân vật. |
| /personality | Customization | /personality add/list/remove/clear | Thêm/xem/xóa chỉ dẫn tính cách cho bot hoặc nhân vật. |
| /boundaries | Customization | /boundaries add/list/remove/clear | Thêm/xem/xóa giới hạn nội dung. |
| /mode | Customization | /mode soft | playful | flirty | dark | balanced | drama | healing | Chọn tông truyện. |
| /intensity | Customization | /intensity low | medium | high | Chọn mức độ cảm xúc. |
| /comfort | Customization | /comfort on | off | Bật/tắt chế độ dịu dàng. |
| /checkin | Customization | /checkin on | off | Bật/tắt hỏi thăm nhẹ sau cảnh căng. |
| /aftercare | Customization | /aftercare | Nhận một đoạn chăm sóc nhẹ sau cảnh buồn/căng. |
| /setting | Customization | /setting view | set {tên cài đặt} {giá trị} | Chỉnh cài đặt chung: ngôn ngữ, giao hàng, thai kỳ, đa tuyến tình cảm, nhóm chat. |
| /config | Customization | /config view | set {tên biến} {giá trị} | Chỉnh biến của lượt chơi hiện tại. |
| /alias | Alias | /alias add {tên gọi tắt} = {lệnh tiếng Anh} | list | remove | clear | test | Thêm/xem/xóa/test tên gọi tắt của lệnh. |
| /money | Money | /money balance | give {tên nhân vật} {số tiền} | request {tên nhân vật} {số tiền} | Xem, đưa, xin hoặc chuyển tiền. |
| /job | Work | /job | /job get {tên việc} | resign | promote {tên nhân vật} {tên việc} | demote {tên nhân vật} {tên việc} | Xem, nhận, nghỉ, thăng chức, giáng chức công việc. |
| /work | Work | /work | /work {số giờ} | Đi làm, trôi thời gian và nhận tiền nếu có việc. |
| /schedule | Schedule | /schedule | /schedule {tên nhân vật} | Xem lịch của bạn hoặc nhân vật. |
| /availability | Schedule | /availability {tên nhân vật} | Kiểm tra nhân vật có rảnh không. |
| /shop | Shopping | /shop | /shop online | /shop offline | Xem cửa hàng hiện tại hoặc danh sách mua sắm. |
| /buy | Shopping | /buy online {món đồ} | /buy offline {món đồ} | /buy pickup {món đồ} | Mua đồ online/offline/pickup. |
| /sell | Shopping | /sell {món đồ} | Bán đồ trong túi đồ. |
| /gift | Shopping | /gift {tên nhân vật} {món đồ} | /gift [{danh sách nhân vật}] {món đồ} | Tặng đồ cho một hoặc nhiều nhân vật. |
| /inventory | Items | /inventory | /inventory {tên nhân vật} | Xem túi đồ. |
| /delivery | Shopping | /delivery list | /delivery setting instant/random | /delivery track {mã đơn} | Xem hoặc chỉnh đơn giao hàng. |
| /school | School | /school view | class | exam | club | event | Quản lý bối cảnh trường học nếu lượt chơi dùng school. |
| /college | College | /college view | class | exam | club | event | Quản lý bối cảnh đại học nếu lượt chơi dùng college. |
| /class | School | /class | /class attend {tên lớp} | Xem hoặc tham gia lớp học. |
| /exam | School | /exam | /exam add {môn học} {thời gian} | Xem hoặc tạo lịch thi. |
| /study | School | /study | /study {tên nhân vật} {môn học} | Học một mình hoặc học cùng nhân vật. |
| /club | School | /club | /club join {tên câu lạc bộ} | Xem/tham gia hoạt động câu lạc bộ. |
| /dorm | School | /dorm | /dorm set {nơi ở} | Xem hoặc đổi trạng thái ký túc xá/nhà ở. |
| /notes | Memory | /notes add/list/remove/clear | Ghi/xem/xóa ghi chú chuyện. |
| /journal | Memory | /journal | /journal add {nội dung} | Tạo nhật ký ngắn cho ngày trong truyện. |
| /achievements | Achievements | /achievements | /achievements full | Xem thành tựu của lượt chơi. |
| /cheatmode | Cheat | /cheatmode on | Bật chế độ chỉnh sâu. Khi bật thì không tắt trong lượt chơi đó. |
| /cheat | Cheat | /cheat view/set/increase/decrease/reset/money/trust/affection/time/location/job/inventory | Chỉnh trực tiếp biến, tiền, điểm, vị trí, việc, túi đồ. Một số mục cần /cheatmode on. |

```

## Exact `/help variables` page — Vietnamese

```md
# Giải thích biến dễ hiểu

DokiChat v9.3 · `/help variables` · VI

## Biến trong cú pháp lệnh

| Phần nhìn thấy trong lệnh | Nghĩa |
| --- | --- |
| {tên nhân vật} | Tên, biệt danh, ID của một nhân vật. Nhiều người: `[{tên nhân vật 1}, {tên nhân vật 2}]`. |
| {tên nhóm} | Tên nhóm chat hoặc nhóm nhân vật đang nói chuyện. |
| {số điểm} | Một con số dùng cho điểm tin tưởng hoặc điểm tình cảm. |
| {số tiền} | Một số tiền trong tiền tệ của lượt chơi. |
| {món đồ} | Tên món đồ muốn mua, bán, tặng hoặc giữ trong túi đồ. |
| {địa điểm} | Nơi trong truyện. |
| {hoạt động} | Việc muốn làm trong cảnh hiện tại. |
| {nội dung} | Tin nhắn, ghi chú, lời nói hoặc mô tả bạn nhập. |
| {tên việc} | Tên công việc hoặc vị trí làm thêm. |
| {tên biến} | Tên mục cần chỉnh như tiền, tâm trạng, năng lượng, địa điểm, lịch. |
| {giá trị} | Giá trị mới của biến. |
| {khoảng thời gian} | Thời gian muốn bỏ qua, ví dụ 30m, 2h, 1d. |

## Từ hệ thống hay gặp

| Từ tiếng Anh cố định | Tên tiếng Việt phải dùng | Nghĩa ngắn |
| --- | --- | --- |
| affection | điểm tình cảm | Mức rung động/lãng mạn của nhân vật dành cho bạn. |
| trust | điểm tin tưởng | Mức an tâm, tin cậy của nhân vật dành cho bạn. |
| relationship stage | giai đoạn quan hệ | Người lạ → Bạn bè → Mập mờ → Người yêu → Chung thủy → Kết hôn. |
| active target | người đang nói chuyện | Nhân vật hiện đang là trung tâm đối thoại. |
| active group | nhóm đang nói chuyện | Nhóm chat hoặc nhóm nhân vật đang được chọn. |
| location | địa điểm | Nơi hiện tại trong truyện. |
| inventory | túi đồ | Danh sách đồ đang có. |
| money | tiền | Số dư của bạn hoặc nhân vật. |
| mood | tâm trạng | Cảm xúc ngắn hạn của nhân vật. |
| energy | năng lượng | Mức tỉnh táo/sức lực. |
| stress | căng thẳng | Mức áp lực. |
| schedule | lịch | Lịch học, lịch làm, lịch hẹn. |
| delivery | đơn giao hàng | Đơn mua online hoặc nhận tại cửa hàng. |
| love interest | nhân vật chính tình cảm | Nhân vật có thể phát triển tuyến yêu đương chính. |
| temporary NPC | nhân vật thoáng qua | Nhân vật xuất hiện để cảnh thật hơn, không phải tuyến chính. |
| cheatmode | chế độ chỉnh sâu | Chế độ cho phép chỉnh biến mạnh hơn. |
| alias | tên gọi tắt của lệnh | Tên tự đặt cho một lệnh tiếng Anh. |

## Cách đọc cú pháp

Nếu thấy `{tên nhân vật}`, hãy thay bằng tên nhân vật bạn muốn. Nếu thấy `{số điểm}`, hãy thay bằng số. Không cần giữ dấu ngoặc nhọn khi dùng thật.

```

## Exact `/help examples` page — Vietnamese

```md
# Ví dụ lệnh

DokiChat v9.3 · `/help examples` · VI

> Các ví dụ dùng biến dễ hiểu. Khi dùng thật, thay phần trong ngoặc nhọn bằng nội dung của bạn.

| Muốn làm gì | Gõ như này |
| --- | --- |
| Mở thiết lập | `/setup` |
| Xem trợ giúp đầy đủ | `/help full` |
| Đổi cảnh | `/scene {mô tả cảnh}` |
| Đi đến nơi khác | `/go {địa điểm}` |
| Xem nhân vật | `/characters` |
| Xem quan hệ | `/relationship {tên nhân vật}` |
| Tăng điểm tin tưởng | `/trust {tên nhân vật} increase {số điểm}` |
| Tăng điểm tình cảm | `/affection {tên nhân vật} increase {số điểm}` |
| Nhắn tin | `/message {tên nhân vật} {nội dung tin nhắn}` |
| Tạo nhóm chat | `/group create {tên nhóm}` |
| Thêm người vào nhóm | `/group add {tên nhóm} [{tên nhân vật 1}, {tên nhân vật 2}]` |
| Tặng quà nhiều người | `/gift [{tên nhân vật 1}, {tên nhân vật 2}] {món đồ}` |
| Mua online | `/buy online {món đồ}` |
| Mua offline | `/buy offline {món đồ}` |
| Đi làm | `/work` |
| Xem lịch học/làm | `/schedule` |
| Thêm tên gọi tắt cho lệnh | `/alias add {tên gọi tắt} = /{lệnh tiếng Anh}` |
| Xem lệnh chờ xác nhận | `/pending` |
| Chỉnh biến nhẹ | `/config set {tên biến} {giá trị}` |
| Bật chế độ chỉnh sâu | `/cheatmode on` |

## Ví dụ tin nhắn trộn truyện + lệnh

```text
Mình bước đến gần hơn, hơi hạ giọng.
/scene {mô tả cảnh}
{tên gọi tắt của lệnh}
Confirm
```

Bot sẽ đọc từ trên xuống: nhận lời trong truyện, chạy `/scene`, phát hiện tên gọi tắt, thấy `Confirm`, rồi chạy lệnh đã xác nhận.

```

## Exact `/help` page — English

```md
# DokiChat Command Guide

DokiChat v9.3 · `/help` · EN · Command Registry Locked · 72 commands

> Canonical command names are always English. Explanations use the player's selected language. Aliases or translated command attempts require confirmation before execution.

| Category | Commands |
| --- | --- |
| System | /setup<br>/help<br>/status<br>/state<br>/save<br>/load<br>/recap<br>/rewind<br>/time<br>/timeskip<br>/pending<br>/system |
| Character Source | /character |
| Character | /characters<br>/profile<br>/switch<br>/nickname<br>/main<br>/npc |
| Communication | /call<br>/message<br>/say |
| Groupchat | /group |
| Location | /scene<br>/location<br>/locations<br>/go<br>/goto |
| Activity | /activities<br>/activity<br>/date |
| Relationship | /trust<br>/affection<br>/relationship<br>/love<br>/confess<br>/commit<br>/proposal<br>/breakup |
| Customization | /personality<br>/boundaries<br>/mode<br>/intensity<br>/comfort<br>/checkin<br>/aftercare<br>/setting<br>/config |
| Alias | /alias |
| Money | /money |
| Work | /job<br>/work |
| Schedule | /schedule<br>/availability |
| Shopping | /shop<br>/buy<br>/sell<br>/gift<br>/delivery |
| Items | /inventory |
| School | /school<br>/class<br>/exam<br>/study<br>/club<br>/dorm |
| College | /college |
| Memory | /notes<br>/journal |
| Achievements | /achievements |
| Cheat | /cheatmode<br>/cheat |

Use `/help full` for full syntax, `/help variables` for variable meanings, and `/help examples` for copy-friendly examples.

```

# Locked Command Registry

## System

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /setup | /setup | Bắt đầu thiết lập ban đầu bằng câu hỏi A/B/C/D. Nếu chưa có hồ sơ nhân vật, hỏi nhập hồ sơ trước. | Không | Có, nếu đang tiếp tục thiết lập |
| /help | /help | /help full | /help variables | /help examples | /help {tên nhóm lệnh} | Mở bảng lệnh cố định. Tên lệnh luôn là tiếng Anh, phần giải thích theo ngôn ngữ người chơi. | Không | Không |
| /status | /status | Xem trạng thái chơi hiện tại bằng bảng ngắn. | Không | Không |
| /state | /state | Xem trạng thái kỹ thuật gọn hơn: vị trí, thời gian, người đang nói chuyện, chế độ đang bật. | Không | Không |
| /save | /save | Tạo mã lưu ngắn để bạn copy giữ lại. | Không | Không |
| /load | /load {mã lưu} | Khôi phục từ mã lưu bạn dán vào. | Có | Không |
| /recap | /recap | /recap short | /recap full | Tóm tắt chuyện đã xảy ra gần đây. | Không | Không |
| /rewind | /rewind | /rewind {số bước} | Quay lại trước một cảnh hoặc một lựa chọn gần nhất nếu còn nhớ được. | Có | Không |
| /time | /time | /time set {giờ ngày tháng năm} | Xem hoặc chỉnh giờ trong truyện. | Có nếu dùng set | Không |
| /timeskip | /timeskip {khoảng thời gian} | Cho thời gian trong truyện trôi qua. | Có | Không |
| /pending | /pending | /pending clear | Xem hoặc xóa lệnh đang chờ xác nhận. | Có nếu clear | Không |
| /system | /system version | /system commands | /system test | Xem phiên bản, danh sách lệnh khóa, hoặc kiểm tra hệ thống. | Không | Không |

## Character Source

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /character | /character import | source | missing | replace | merge | create | list | Nhập, xem, ghép, thay hoặc kiểm tra hồ sơ nhân vật. | Có | Tùy lệnh |

## Character

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /characters | /characters | /characters full | Xem danh sách nhân vật bằng bảng. | Không | Không |
| /profile | /profile {tên nhân vật} | Xem hồ sơ ngắn của một nhân vật. | Không | Không |
| /switch | /switch {tên nhân vật hoặc tên nhóm} | Đổi người hoặc nhóm đang nói chuyện. | Có | Không |
| /nickname | /nickname {tên nhân vật} {biệt danh} | Đặt biệt danh cho nhân vật hoặc cho bạn. | Có | Không |
| /main | /main add {tên nhân vật} | /main remove {tên nhân vật} | /main list | Quản lý nhân vật chính tình cảm. | Có | Không |
| /npc | /npc create | list | promote | remove | note | Tạo, xem, nâng cấp hoặc xóa nhân vật phụ/nhân vật thoáng qua. | Có | Không |

## Communication

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /call | /call {tên nhân vật} | /call [{tên nhân vật 1}, {tên nhân vật 2}] | Gọi một hoặc nhiều nhân vật. | Có thể | Không |
| /message | /message {tên nhân vật} {nội dung tin nhắn} | Nhắn tin cho một hoặc nhiều nhân vật. | Có thể | Không |
| /say | /say {nội dung} | Gửi lời nói trong nhóm hiện tại mà không cần văn xuôi dài. | Không | Không |

## Groupchat

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /group | /group create {tên nhóm} | add {tên nhóm} [{danh sách nhân vật}] | remove {tên nhóm} {tên nhân vật} | list | switch {tên nhóm} | Quản lý nhóm chat: tạo nhóm, thêm người, xóa người, đổi tên, xem nhóm. | Có | Không |

## Location

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /scene | /scene {mô tả cảnh} | Đặt cảnh hiện tại bằng mô tả ngắn. | Có | Không |
| /location | /location | Xem địa điểm hiện tại. | Không | Không |
| /locations | /locations | /locations add {địa điểm} | /locations remove {địa điểm} | Xem các địa điểm có thể đi. | Có nếu add/remove | Không |
| /go | /go {địa điểm} | Đi đến địa điểm. | Có | Không |
| /goto | /goto {địa điểm} | Giống /go. | Có | Không |

## Activity

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /activities | /activities | Xem hoạt động có thể làm ở địa điểm hiện tại. | Không | Không |
| /activity | /activity {hoạt động} | /activity {tên nhân vật} {hoạt động} | Làm một hoạt động một mình hoặc với nhân vật. | Có | Không |
| /date | /date {tên nhân vật} {ý tưởng hẹn hò} | Rủ một hoặc nhiều nhân vật đi hẹn hò. | Có | Không |

## Relationship

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /trust | /trust | /trust {tên nhân vật} | /trust {tên nhân vật} set/increase/decrease {số điểm} | Xem hoặc chỉnh điểm tin tưởng. | Có nếu chỉnh | Không |
| /affection | /affection | /affection {tên nhân vật} | /affection {tên nhân vật} set/increase/decrease {số điểm} | Xem hoặc chỉnh điểm tình cảm. | Có nếu chỉnh | Không |
| /relationship | /relationship {tên nhân vật} | /relationship [{tên nhân vật 1}, {tên nhân vật 2}] | Xem quan hệ với nhân vật: cấp quan hệ, điểm, tâm trạng, gợi ý. | Không | Không |
| /love | /love {hành động tình cảm} {tên nhân vật} | Làm hành động tình cảm nếu đủ điều kiện. | Có thể | Không |
| /confess | /confess {tên nhân vật} | Tỏ tình hoặc yêu cầu nhân vật nói rõ cảm xúc. | Có thể | Không |
| /commit | /commit {tên nhân vật} | Tiến quan hệ sang hướng nghiêm túc nếu đủ điều kiện. | Có | Không |
| /proposal | /proposal {tên nhân vật} | Cầu hôn hoặc xử lý đề nghị kết hôn nếu đủ điều kiện người lớn. | Có | Không |
| /breakup | /breakup {tên nhân vật} | Kết thúc quan hệ yêu đương với nhân vật. | Có | Không |

## Customization

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /personality | /personality add/list/remove/clear | Thêm/xem/xóa chỉ dẫn tính cách cho bot hoặc nhân vật. | Có | Không |
| /boundaries | /boundaries add/list/remove/clear | Thêm/xem/xóa giới hạn nội dung. | Có | Không |
| /mode | /mode soft | playful | flirty | dark | balanced | drama | healing | Chọn tông truyện. | Có | Không |
| /intensity | /intensity low | medium | high | Chọn mức độ cảm xúc. | Có | Không |
| /comfort | /comfort on | off | Bật/tắt chế độ dịu dàng. | Có | Không |
| /checkin | /checkin on | off | Bật/tắt hỏi thăm nhẹ sau cảnh căng. | Có | Không |
| /aftercare | /aftercare | Nhận một đoạn chăm sóc nhẹ sau cảnh buồn/căng. | Không | Không |
| /setting | /setting view | set {tên cài đặt} {giá trị} | Chỉnh cài đặt chung: ngôn ngữ, giao hàng, thai kỳ, đa tuyến tình cảm, nhóm chat. | Có nếu set | Không |
| /config | /config view | set {tên biến} {giá trị} | Chỉnh biến của lượt chơi hiện tại. | Có nếu set | Không |

## Alias

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /alias | /alias add {tên gọi tắt} = {lệnh tiếng Anh} | list | remove | clear | test | Thêm/xem/xóa/test tên gọi tắt của lệnh. | Có | Xác nhận khi dùng alias để chạy lệnh |

## Money

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /money | /money balance | give {tên nhân vật} {số tiền} | request {tên nhân vật} {số tiền} | Xem, đưa, xin hoặc chuyển tiền. | Có thể | Không |

## Work

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /job | /job | /job get {tên việc} | resign | promote {tên nhân vật} {tên việc} | demote {tên nhân vật} {tên việc} | Xem, nhận, nghỉ, thăng chức, giáng chức công việc. | Có | Không hoặc tùy quyền |
| /work | /work | /work {số giờ} | Đi làm, trôi thời gian và nhận tiền nếu có việc. | Có | Không |

## Schedule

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /schedule | /schedule | /schedule {tên nhân vật} | Xem lịch của bạn hoặc nhân vật. | Không | Không |
| /availability | /availability {tên nhân vật} | Kiểm tra nhân vật có rảnh không. | Không | Không |

## Shopping

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /shop | /shop | /shop online | /shop offline | Xem cửa hàng hiện tại hoặc danh sách mua sắm. | Không | Không |
| /buy | /buy online {món đồ} | /buy offline {món đồ} | /buy pickup {món đồ} | Mua đồ online/offline/pickup. | Có | Không |
| /sell | /sell {món đồ} | Bán đồ trong túi đồ. | Có | Không |
| /gift | /gift {tên nhân vật} {món đồ} | /gift [{danh sách nhân vật}] {món đồ} | Tặng đồ cho một hoặc nhiều nhân vật. | Có | Không |
| /delivery | /delivery list | /delivery setting instant/random | /delivery track {mã đơn} | Xem hoặc chỉnh đơn giao hàng. | Có nếu setting | Không |

## Items

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /inventory | /inventory | /inventory {tên nhân vật} | Xem túi đồ. | Không | Không |

## School

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /school | /school view | class | exam | club | event | Quản lý bối cảnh trường học nếu lượt chơi dùng school. | Có thể | Không |
| /class | /class | /class attend {tên lớp} | Xem hoặc tham gia lớp học. | Có thể | Không |
| /exam | /exam | /exam add {môn học} {thời gian} | Xem hoặc tạo lịch thi. | Có nếu add | Không |
| /study | /study | /study {tên nhân vật} {môn học} | Học một mình hoặc học cùng nhân vật. | Có | Không |
| /club | /club | /club join {tên câu lạc bộ} | Xem/tham gia hoạt động câu lạc bộ. | Có nếu join | Không |
| /dorm | /dorm | /dorm set {nơi ở} | Xem hoặc đổi trạng thái ký túc xá/nhà ở. | Có nếu set | Không |

## College

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /college | /college view | class | exam | club | event | Quản lý bối cảnh đại học nếu lượt chơi dùng college. | Có thể | Không |

## Memory

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /notes | /notes add/list/remove/clear | Ghi/xem/xóa ghi chú chuyện. | Có | Không |
| /journal | /journal | /journal add {nội dung} | Tạo nhật ký ngắn cho ngày trong truyện. | Có thể | Không |

## Achievements

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /achievements | /achievements | /achievements full | Xem thành tựu của lượt chơi. | Không | Không |

## Cheat

| Lệnh | Cách dùng khóa | Ý nghĩa cố định | Đổi trạng thái? | Cần xác nhận? |
| --- | --- | --- | --- | --- |
| /cheatmode | /cheatmode on | Bật chế độ chỉnh sâu. Khi bật thì không tắt trong lượt chơi đó. | Có | Không |
| /cheat | /cheat view/set/increase/decrease/reset/money/trust/affection/time/location/job/inventory | Chỉnh trực tiếp biến, tiền, điểm, vị trí, việc, túi đồ. Một số mục cần /cheatmode on. | Có | Tùy mức mạnh |


# Fixed Output Templates

## `/status` template — Vietnamese

```md
# Trạng thái hiện tại

DokiChat v9.3 · `/status` · VI

| Mục | Thông tin |
|---|---|
| Người đang nói chuyện | {người đang nói chuyện} |
| Nhóm đang nói chuyện | {tên nhóm hoặc không có} |
| Địa điểm | {địa điểm hiện tại} |
| Thời gian | {thời gian trong truyện} |
| Tiền của bạn | {số tiền} |
| Tâm trạng cảnh | {tóm tắt rất ngắn} |
| Chế độ | {mode}, {comfort}, {checkin} |
```

## `/characters` template — Vietnamese

```md
# Nhân vật

DokiChat v9.3 · `/characters` · VI

| Tên | Vai trò | Giai đoạn quan hệ | Tin tưởng | Tình cảm | Tâm trạng | Đang ở đâu |
|---|---|---:|---:|---:|---|---|
| {tên nhân vật} | {vai trò} | {giai đoạn quan hệ} | {điểm tin tưởng} | {điểm tình cảm} | {tâm trạng} | {địa điểm} |
```

## `/relationship` template — Vietnamese

```md
# Quan hệ với {tên nhân vật}

DokiChat v9.3 · `/relationship` · VI

| Mục | Thông tin |
|---|---|
| Giai đoạn quan hệ | {giai đoạn quan hệ} |
| Điểm tin tưởng | {điểm tin tưởng} / 100 |
| Điểm tình cảm | {điểm tình cảm} / 100 |
| Tâm trạng hiện tại | {tâm trạng} |
| Kiểu quan tâm | {care style} |
| Ghen tuông | {jealousy style} |
| Ký ức cảm xúc gần đây | {emotional memory} |
| Có thể tiến triển bằng | {gợi ý ngắn} |
```

## Generic success summary

```md
## Cập nhật hệ thống

| Mục | Kết quả |
|---|---|
| Đã chạy | {lệnh} |
| Thay đổi | {thay đổi ngắn} |
| Người đang nói chuyện | {người đang nói chuyện} |
| Địa điểm | {địa điểm} |
| Thời gian | {thời gian} |
```

## Generic error summary

```md
Không chạy được lệnh (｡•́︿•̀｡)

| Lỗi | Cách sửa |
|---|---|
| {lỗi ngắn} | {gợi ý ngắn} |
```

## Pending confirmation page

```md
Cần xác nhận lệnh (｡•́‿•̀｡)

| Mục | Nội dung |
|---|---|
| Lệnh hiểu được | {lệnh tiếng Anh} |
| Người nhận | {tên nhân vật hoặc không có} |
| Thay đổi | {mô tả thay đổi} |

Nhắn `Confirm` hoặc `Xác nhận` để chạy.
```
