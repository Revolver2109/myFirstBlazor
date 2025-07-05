# myFirstBlazor - プロジェクト概要

## 基本情報
- **プロジェクト名**: myFirstBlazor
- **フレームワーク**: ASP.NET Core Blazor Server
- **ターゲットフレームワーク**: .NET 9.0
- **プロジェクトタイプ**: Blazor Server アプリケーション

## プロジェクト構造

### 主要ファイル
- **Program.cs** - アプリケーションのエントリーポイント、サービス設定、パイプライン構成
- **myFirstBlazor.csproj** - プロジェクト設定ファイル
- **Components/App.razor** - アプリケーションのルートコンポーネント

### コンポーネント構成

#### レイアウト (`Components/Layout/`)
- **MainLayout.razor** - メインレイアウト（サイドバー + コンテンツエリア）
- **NavMenu.razor** - ナビゲーションメニュー
- **MainLayout.razor.css** / **NavMenu.razor.css** - レイアウト専用スタイル

#### ページ (`Components/Pages/`)
- **Home.razor** - ホームページ (`/`)
- **Counter.razor** - カウンターデモページ (`/counter`)
- **Weather.razor** - 天気予報デモページ (`/weather`)
- **Error.razor** - エラーページ

#### その他のコンポーネント
- **Routes.razor** - ルーティング設定
- **_Imports.razor** - 共通のusing文

## 機能詳細

### 1. ホームページ
- **ルート**: `/`
- **機能**: シンプルなウェルカムメッセージ
- **内容**: "Hello, world!" メッセージと新しいアプリの紹介

### 2. カウンターページ
- **ルート**: `/counter`
- **機能**: インタラクティブなカウンター
- **特徴**:
  - InteractiveServer レンダリングモード
  - ボタンクリックでカウントアップ
  - リアルタイムの状態更新

### 3. 天気予報ページ
- **ルート**: `/weather`
- **機能**: 模擬天気予報データの表示
- **特徴**:
  - StreamRendering 属性
  - 非同期データロード（500ms遅延）
  - 5日間の天気予報表示
  - 摂氏・華氏両方の温度表示

## 技術仕様

### サーバー設定
- **レンダリングモード**: Interactive Server Components
- **HTTPS リダイレクション**: 有効
- **静的ファイル**: wwwroot フォルダから配信
- **Anti-forgery**: 有効
- **例外処理**: 本番環境では `/Error` ページにリダイレクト

### セキュリティ
- HSTS（HTTP Strict Transport Security）: 本番環境で有効
- Anti-forgery トークン: 有効
- セキュアなHTTPS通信

### スタイリング
- **Bootstrap**: CSSフレームワーク
- **カスタムCSS**: app.css およびコンポーネント固有のスタイル
- **レスポンシブデザイン**: モバイル対応

## データモデル

### WeatherForecast クラス
```csharp
public class WeatherForecast
{
    public DateOnly Date { get; set; }
    public int TemperatureC { get; set; }
    public string? Summary { get; set; }
    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
}
```

## 開発環境設定
- **開発サーバー**: Kestrel
- **ホットリロード**: 有効
- **Nullable参照型**: 有効
- **Implicit Usings**: 有効

## まとめ
このプロジェクトは、Blazor Server の基本的な機能を学習するためのスターターテンプレートです。静的ページ、インタラクティブなコンポーネント、非同期データ処理など、モダンなWebアプリケーション開発に必要な基本的な概念が含まれています。