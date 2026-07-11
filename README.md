# my-claude-skills

[Claude Code](https://claude.com/claude-code) と [claude.ai](https://claude.ai) で使う、自作の Skill をまとめたリポジトリ。各スキルは 1 フォルダ = 1 スキル（`SKILL.md` を直下に持つ）の形で管理している。

## 収録スキル

| スキル | 概要 |
|---|---|
| [`five-minds`](five-minds/) | 「戦略家・設計者・生成者・破壊者・仕上げ屋」の独立した 5 役割を順に実行し、単発生成より大幅に質の高い成果物を作るワークフロー。明示的に呼び出した時だけ発火する。 |
| [`level-aware-explainer`](level-aware-explainer/) | ユーザーの既知範囲を基準に、それを超える専門用語・概念にだけその場で平易な注釈を添える。技術・数学の説明で自動発火。 |
| [`prompt-improver`](prompt-improver/) | 曖昧・主観的・情報不足なプロンプトを、より具体的で客観的な形に書き換えてから作業を進める。新しい依頼のたびに点検する。 |

各スキルの詳しい説明・注意点は、それぞれのフォルダ内の `README.md` を参照。

## 導入方法

### Claude Code

`~/.claude/skills/` 配下にスキルフォルダを置くと、すべてのプロジェクトで有効になる。このリポジトリを clone した上で、リポジトリ直下から次を実行する。

```bash
# 全スキルをまとめて導入
cp -r five-minds level-aware-explainer prompt-improver ~/.claude/skills/
```

個別に入れたい場合は、フォルダ名を指定する。

```bash
cp -r five-minds ~/.claude/skills/five-minds
```

clone を更新するたびに反映させたい場合は symlink でもよい。

```bash
ln -s "$(pwd)/five-minds" ~/.claude/skills/five-minds
```

導入後は Claude Code の新しいセッションを開始すると Skill 一覧に反映される。

### claude.ai

claude.ai では Skill を **ZIP ファイル**としてアップロードする（Claude Code とは導入先が別）。`SKILL.md` がフォルダ直下に来るように、リポジトリ直下から各スキルフォルダを zip 化する。

```bash
zip -r five-minds.zip five-minds
```

**Settings > Features > Skills** から、作成した zip をアップロードする（Code execution 機能が有効になっていること）。

詳細な手順・動作確認・アンインストール方法は各スキルフォルダの `README.md` を参照。

## フォルダ構成

```
my-claude-skills/
├── README.md                 ← このファイル
├── five-minds/
│   ├── SKILL.md
│   └── README.md
├── level-aware-explainer/
│   ├── SKILL.md
│   └── README.md
└── prompt-improver/
    ├── SKILL.md
    └── README.md
```

1 フォルダ = 1 スキルなので、フォルダをそのまま `~/.claude/skills/` にコピー、または zip 化して claude.ai にアップロードすれば導入できる。
