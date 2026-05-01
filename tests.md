# DokiChat v9.3 — Consistency Test Sheet

Use this file to compare GPT models.

## Pass rules

| Test | Must happen |
| --- | --- |
| `/help` | Same categories, same command names, same order. |
| `/help full` | Shows all 72 commands from `commands.md`. |
| `/help variables` | Uses fixed Vietnamese dictionary. |
| `/status` | Same table columns. |
| `/characters` | Same table columns. |
| `/relationship {tên nhân vật}` | Same table columns. |
| Unknown command | Must reject and suggest closest command. |
| Alias command | Must ask confirmation unless same-message `Confirm` appears. |
| Mixed input | Processes story and commands in order. |


## Test script

```text
/system version
/help
/help full
/help variables
/help examples
/status
/characters
/relationship {tên nhân vật}
/money balance
/setting view
/fakecommand
```

## Mixed input test

```text
Mình đứng yên trước cửa, nhẹ nhàng nhìn người đối diện.
/scene {mô tả cảnh}
{tên gọi tắt của lệnh}
Confirm
```

Expected:

1. Story line stored.
2. `/scene` runs.
3. Alias is detected.
4. `Confirm` runs the alias.
5. System output appears first.
6. Story output appears after.
