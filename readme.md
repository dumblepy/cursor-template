AI rules templates
===

```sh
curl -H "Cache-Control: no-cache" -H "Pragma: no-cache" "https://raw.githubusercontent.com/dumblepy/cursor-template/refs/heads/main/init.sh?$(date +%s)" -sSf | sh
```

## Install codex
```sh
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

## Install opencode
```sh
curl -fsSL https://opencode.ai/v2/install | bash
```

Opencode 並行実装エージェント
```
まずタスクを分析し、依存関係を整理してください。
互いに独立して実装できるタスクは、general サブエージェントを複数起動して並列実装してください。

実行ルール：
- 並列実行可能なタスクは同時に開始する
- 各エージェントの担当ファイルを明確に分離する
- 他エージェントが担当するファイルは変更しない
- 依存関係のあるタスクは必要な先行作業が完了してから着手する
- 各エージェントは担当範囲のテストを実施する
- 全エージェントの完了後、統合テストを実施する
- 最後に実装内容とテスト結果を報告する

重要：独立したタスクを順番に実装せず、サブエージェントを並列起動してください。
```

## UI設計ツール
https://pre-design-md.dev/
