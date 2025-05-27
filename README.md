## プロジェクト概要

複数のDjangoアプリケーションを統合した学習用プロジェクトで、以下の機能を実装しています：

- **ブログアプリ（blogapp）**: 記事の投稿・閲覧機能
- **アカウント管理（accounts）**: ユーザー認証・プロフィール管理

## 技術スタック

- **Backend**: Django
- **Database**: SQLite（開発環境）
- **Frontend**: HTML, CSS, Bootstrap
- **Python**: 3.8.10

## セットアップ手順

### 1. リポジトリのクローン

```bash
git clone https://github.com/Raisei-Ito/Created-by-django.git
cd Created-by-django
```

### 2. 仮想環境の作成と有効化

```bash
# 仮想環境の作成
python -m venv venv

# 仮想環境の有効化
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
```

### 3. 依存関係のインストール

```bash
# Djangoのインストール
pip install django

# その他必要なパッケージがある場合
# pip install -r requirements.txt
```

### 4. データベースのセットアップ

```bash
# マイグレーションファイルの作成
python manage.py makemigrations

# データベースにマイグレーションを適用
python manage.py migrate
```

### 5. スーパーユーザーの作成（オプション）

```bash
python manage.py createsuperuser
```

### 6. 開発サーバーの起動

```bash
python manage.py runserver
```

ブラウザで `http://127.0.0.1:8000/` にアクセスしてアプリケーションを確認できます。

## 主な機能

### ブログアプリ（blogapp）
- 記事の作成、編集、削除
- 記事の一覧表示
- 記事の詳細表示

### アカウント管理（accounts）
- ユーザー登録
- ログイン・ログアウト
- プロフィール管理

### いいね・既読機能
- いいねの数の表示、既読した人の数の表示

## 管理画面

Django管理画面にアクセスするには：

1. スーパーユーザーを作成（上記手順5参照）
2. `http://127.0.0.1:8000/admin/` にアクセス
3. 作成したスーパーユーザーでログイン

## 学習内容

このプロジェクトを通じて以下のDjangoの概念を学習した：

- Djangoプロジェクトの構造と設定
- モデル（Model）の定義とデータベース操作
- ビュー（View）の実装
- テンプレート（Template）の作成
- URL設定とルーティング
- ユーザー認証システム
- 静的ファイルの管理
- Django管理画面の活用

## 本番環境でのデプロイ

本番環境では以下の流れでデプロイを行います。

- **whitenoiseを使用した静的ファイルのアップロード**  
  `whitenoise` を導入することで、Django アプリが静的ファイル（CSSやJS、画像など）を自身で直接配信できるようになります。
  ```bash
  pip install whitenoise
  ```
- **collectstaticを使用して、静的ファイルを一か所にまとめる**  
  `python manage.py collectstatic` を実行し、各アプリ内に散らばっている静的ファイルを `STATIC_ROOT` にまとめます。

- **Procfileの準備**  
  HerokuでDjangoを動かすために、プロジェクトのルートディレクトリに `Procfile` を作成し、以下の内容を記述します：

  ```
  web: gunicorn プロジェクト名.wsgi --log-file -
  ```
  ※ `プロジェクト名` は `manage.py` があるディレクトリ名を指定します。

- **requirements.txtの準備**  
  Herokuに必要なPythonパッケージを伝えるため、 `requirements.txt` を作成します：

- **作成したアプリをGitHubのリポジトリにアップロードする**  
  作成したDjangoアプリのコードをGitHubリポジトリにプッシュします。

- **GitHubリポジトリからHerokuでデプロイする**  
  HerokuのダッシュボードまたはCLIからGitHubリポジトリを連携させ、デプロイを実行します。

- **Heroku環境変数の設定**  
  Heroku上では `SECRET_KEY` や `DEBUG=False` などの設定を環境変数（Config Vars）として登録し、本番用の安全な設定で運用します。

## 参考資料
- [django チュートリアル](https://www.youtube.com/playlist?list=PLuCS8p0T7ozK4Ne1e5eAVG2R5Gbs1naix)
- [Udemy講座: Django 3app](https://www.udemy.com/course/django-3app/?couponCode=CP130525JP)
- [Django公式ドキュメント](https://docs.djangoproject.com/)

## 作成者

- GitHub: [@Raisei-Ito](https://github.com/Raisei-Ito)

## 注意事項

- このプロジェクトは学習用途として作成されています
- セキュリティ設定やパフォーマンス最適化は学習範囲に含まれていない場合があります
- 実際の開発では、より厳密なセキュリティ対策や設定が必要です
