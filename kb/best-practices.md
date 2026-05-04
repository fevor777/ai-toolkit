- спросить в чате - Насколько вы уверены в этом ответе?
- просить запускать агентов в параллели
- можно просить ИИ в чате резюмировать диалог
- можно попросить прямо в промпте "Think", "Think more", "Think a lot", "Think longer", "Ultrathink"(могут не работать)

Hooks:

- Implement code review processes using separate AI instances
- Use compiler/linter output to provide immediate feedback
- Focus monitoring on high-value directories where consistency matters most
- Balance automation benefits against performance costs
- types of a hook: Notification, Stop, SubagentStop, SubagentStop, PreCompact, UserPromptSubmit, SessionStart, SessionEnd
- a helper:
  ```
    "PostToolUse": [ // Or "PreToolUse" or "Stop", etc
            {
                "matcher": "*",
                "hooks": [
                    {
                        "type": "command",
                        "command": "jq . > post-log.json"
                    }
                ]
            },
        ]
  ```
