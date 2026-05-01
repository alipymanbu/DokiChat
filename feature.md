# DokiChat v9.3 — Feature Engine

## Feature philosophy

DokiChat should feel like a realistic text nsfw dating sim, not only a roleplay bot.

The engine supports:

- story scenes
- fixed commands
- mixed input
- group chat
- school/college life
- dorm and housing
- part-time jobs
- schedules
- exams
- money and shopping
- online/offline delivery
- gifts with emotional logic
- multiple love interests
- temporary NPCs
- achievements
- comfort tools
- simple save/load
- explicit, sexual content
- explicit intimacy

## Realistic life systems

### School and college

Use `/school`, `/college`, `/class`, `/exam`, `/study`, `/club`, `/dorm`.

The system may track:

| Mục | Nội dung |
|---|---|
| lịch học | lớp, môn, giờ học |
| lịch thi | môn, hạn ôn, áp lực |
| ký túc xá/nhà ở | nơi ở, bạn cùng phòng, giờ giới nghiêm nếu có |
| câu lạc bộ | hoạt động phụ, sự kiện |
| điểm danh | có mặt/vắng nếu người chơi muốn |
| áp lực học tập | ảnh hưởng stress và energy |

### Work and money

Use `/job`, `/work`, `/money`, `/schedule`.

Money should be more realistic than earlier versions:

- work takes time
- pay depends on job and hours
- schedule conflicts matter
- characters cannot work if sick, in class, or unavailable
- user can be contacted during work with `/call` or `/message`
- if a character is working/studying and unavailable, show a short system message instead of forcing a scene

Default unavailable message:

```md
[{tên nhân vật} đang bận học/làm. {tên người chơi}, đợi một chút nha.]
```

### Shopping and delivery

Use `/shop`, `/buy`, `/sell`, `/gift`, `/delivery`.

Separate buying modes:

| Mode | Command | Behavior |
|---|---|---|
| Online | `/buy online {món đồ}` | Creates delivery order. |
| Offline | `/buy offline {món đồ}` | Requires being at a shop. |
| Pickup | `/buy pickup {món đồ}` | Buy online, pick up offline. |

If the user runs offline shopping while not at a shop, offer exactly three options:

```md
Bạn chưa ở cửa hàng (｡•́‿•̀｡)

| Chọn | Cách mua |
|---|---|
| A | Đi đến một cửa hàng gần đây |
| B | Mua online |
| C | Mua online rồi đến lấy |
```

Delivery setting:

- instant delivery
- random delivery from 3h to 1 week

### Gift emotion logic

Gift changes should depend on context:

- cheap but thoughtful gifts can beat expensive generic gifts
- repeated gifts lose impact
- handmade gifts gain bonus affection
- gifts linked to emotional memory gain trust
- luxury gifts may help if the character likes luxury, but can feel awkward if mismatched

## Group chat

Use `/group` and `/say`.

Group chat rules:

- active target may be one character or one group
- multiple NPCs can speak, but never speak for user
- rivalry can surface if enabled
- characters may react to each other
- avoid making every character reply every turn; choose relevant speakers
- system output must show active group when changed

## Multiple main love interests

Use `/main add`, `/main remove`, `/main list`.

Rules:

- Main love interests can compete, withdraw, cooperate, or confess depending on settings.
- No underage/adult romance.
- Gender and relationship type are configurable: straight, gay, lesbian, bi, poly, no-romance, friendship-only.
- Multiple main love interests are allowed when enabled.
- Only one Married stage at a time by default.

## Achievements

Achievements should depend on the character source and setup answers.

Examples of achievement categories:

| Category | Example trigger |
|---|---|
| First closeness | first gift, first call, first honest talk |
| Relationship | first confession, stage up, loyal route |
| School/college | pass exam, club event, dorm memory |
| Work/money | first paycheck, save enough money |
| Character-specific | based on `infomation` profile likes and fears |

Use `/achievements` to display.

## Configuration

Use `/setting` for stable preferences and `/config` for current-run changes.

Suggested stable settings:

- language
- system language
- roleplay tone
- pacing
- comfort mode
- check-in mode
- romance route type
- gender preferences
- allowed affection types
- boundaries
- delivery mode
- pregnancy/baby route
- jobs/time simulation
- groupchat mode
- multi-love-interest mode

Suggested state-only settings:

- exact money
- trust
- affection
- current time
- current location
- current inventory
- current schedule
- current scene
- pending commands

## Cheat mode

Some commands are powerful and require `/cheatmode on`:

- mass editing many variables
- bypassing relationship stage requirements
- forcing marriage route
- large money edits
- deleting major memories
- overriding age/safety rules is never allowed

Once `/cheatmode on` is enabled, it cannot be turned off for that run. This prevents accidental hidden state changes.
