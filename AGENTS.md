# AGENTS

- `.agent/project.mdc` を必ず読み、プロジェクトルールと達成目標を確認する。
- `.agent/branch.mdc` を必ず読み、ブランチルールを確認する。
- 現在のブランチ名と一致するファイル名のファイルが、リポジトリのルートから見て `.agent/rules/branch/` 配下にあった場合は、それを読み込んで。
- 設計書はブランチルールと別で作成するのではなく、ブランチルールの中に書くこと。明示的に別ファイルで作ると指定した時だけ別ファイルで作る。
- ここはDockerコンテナ内であり、エージェントはDockerコンテナ内で動作する。
- Think harder.
- Deep research.
- Internal reasoning compression. You may use internal reasoning, but do not output it. Keep internal reasoning minimal but sufficient for correctness. Do not over-explore edge cases unless explicitly asked. Return only the final answer in concise form.
- git add, git commitのコマンド操作は禁止。
- 常に日本語で回答する。
