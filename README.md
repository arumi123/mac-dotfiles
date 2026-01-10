# macOS Setup

## 構成

```
mac-dotfiles/
├── Brewfile                   # Homebrewパッケージ定義
├── orbstack/
│   └── sandbox.yaml          # OrbStack Sandbox環境
└── README.md                  # このファイル
```

## セットアップ手順

### 1. Homebrewのインストール

### 2. パッケージのインストール

```bash
# brew bundle --global は ~/.Brewfile を固定で読み込むため、シンボリックリンクを作成し、リポジトリ内の設定ファイルを自動的に反映させる

# シンボリックリンクの作成（このリポジトリのルートで実行）
ln -sf $(pwd)/Brewfile ~/.Brewfile

# パッケージのインストール
brew bundle install --global
```

### 3. Colima 仮想マシンの起動

```bash
# colima startの設定ファイルは項目が多く環境依存の内容を含むため、
# 設定ファイルは管理せず、高速化オプションを指定して起動する方法をここに記録する。

# Colima 仮想マシンの起動
colima start \
  --cpu 2 \                 # CPU数（デフォルト: 2）
  --memory 2 \              # メモリ容量（デフォルト: 2GB）
  --disk 60 \               # ストレージ容量（デフォルト: 100GB）
  --vm-type vz \            # Apple Virtualization.Framework使用で高速化（デフォルト: qemu）
  --mount-type virtiofs \   # 最速のマウント方式（デフォルト: sshfs）
  --runtime docker
```

### 4. OrbStack仮想マシンの起動（オプション）

> **注意**: ライセンスを確認し使用するか判断する。そのため、Brewfileには含めない。

```bash
# OrbStackのインストール
brew install --cask orbstack

# OrbStackはデフォルトで読み込む設定ファイルの場所がないため、
# -c オプションでこのリポジトリ内の orbstack/sandbox.yaml を直接指定する

# 仮想マシンの作成（このリポジトリのルートで実行）
orb create ubuntu:22.04 sandbox -c orbstack/sandbox.yaml
```
