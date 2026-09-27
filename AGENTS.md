# AGENTS

- `.agent/rules/project.mdc` を必ず読み、プロジェクトルールと達成目標を確認する。
- `.agent/rules/branch.mdc` を必ず読み、ブランチルールを確認する。
- 現在のブランチ名と一致するファイル名のファイルが、リポジトリのルートから見て `.agent/rules/branch/` 配下にあった場合は、それを読み込んで。
- 設計書はブランチルールと別で作成するのではなく、ブランチルールの中に書くこと。明示的に別ファイルで作ると指定した時だけ別ファイルで作る。
- ここはDockerコンテナ内であり、エージェントはDockerコンテナ内で動作する。
- Think harder.
- Deep research.
- Internal reasoning compression. You may use internal reasoning, but do not output it. Keep internal reasoning minimal but sufficient for correctness. Do not over-explore edge cases unless explicitly asked. Return only the final answer in concise form.
- git add, git commitのコマンド操作は禁止。
- 常に日本語で回答する。

# Autonomous development policy

このプロジェクトでは、タスク実装時に以下の自律ループを完了条件が満たされるまで繰り返す。

## 完了条件の定義

各タスクの完了条件は `.agent/progress.md` に集約する。以下の形式で機械的に検証可能な条件を列挙する。

```text
完了条件:
- <テスト・lint・typecheck・curl 等で実行可能な検証>
- ...
```

現在のプロジェクト全体の完成条件（NISQL-GOAL-001）およびタスク別完了条件は `.agent/progress.md` の「プロジェクト全体の完成条件」「タスク別完了条件」を参照すること。

条件は「コードを見て正しそう」ではなく、**テスト・lint・typecheck・curl・Playwright 等の実行可能な検証**で機械的に判定できるものとする。

## 実装ループ

以下のループを、完了条件をすべて満たすまで自律的に繰り返すこと。

1. 現在のコードとエラーを調査する
2. 原因を仮説化する
3. 最小限の変更を実装する
4. テスト・lint・typecheck・必要な実行確認を行う
5. 失敗した場合はログを分析する
6. 仮説を修正して再実装する
7. 全完了条件を再検証する

テストが失敗した状態で作業を終了しないこと。
一部だけ成功しても終了しないこと。
同じ方法に固執せず、失敗した仮説は捨てて別の方法を試すこと。

## 自律判断基準

ユーザーへの確認が不要な、可逆的なコード変更・調査・テスト・リファクタリングは自律的に進めてよい。

以下の場合だけ停止して質問すること:
- 秘密情報や認証情報が必要
- 外部サービスへの不可逆な操作が必要
- 仕様上、複数の選択肢がありコードから判断不能
- 同一の根本原因について複数の異なるアプローチを試しても進展がない

## 作業記録

長時間作業になる場合は `.agent/progress.md` を維持すること。

各反復ごとに:
- 現在の問題
- 試したこと
- 結果
- 否定された仮説
- 次に試すこと

を短く更新する。

コンテキストが圧縮された場合でも、`.agent/progress.md` と git diff とテスト結果を確認して作業を継続する。

## 完了報告

完了時には以下を報告すること:
- 変更内容
- 原因
- 実行した検証
- 各完了条件の結果
