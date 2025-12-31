# macOS Setup

## 構成

```
mac-dotfiles/
├── Brewfile                   # Homebrewパッケージ定義
├── orbstack/
│   └── sandbox.yaml          # Sandbox環境
└── README.md                  # このファイル
```

## セットアップ手順

### 1. Homebrewのインストール

### 2. パッケージのインストール

```bash
# このリポジトリのディレクトリで実行
brew bundle install
```

### 3. OrbStack 仮想マシンの作成

```bash
orb create ubuntu:22.04 sandbox -c orbstack/sandbox.yaml
```
