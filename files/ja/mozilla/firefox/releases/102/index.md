---
title: Firefox 102 for developers
slug: Mozilla/Firefox/Releases/102
tags:
  - '102'
  - Firefox
  - Mozilla
  - Release
---
{{FirefoxSidebar}}

このページでは、開発者に影響する Firefox 102 の変更点をまとめています。Firefox 102 は、米国時間 2022 年 6 月 28 日にリリースされました。

## ウェブ開発者向けの変更点一覧

### HTML

変更なし。

### CSS

出力端末がコンテンツを表示した後に、その内容を変更できる能力を確認するために使用できる [`update`](/ja/docs/Web/CSS/@media/update-frequency) メディア特性をデフォルトで有効にしました ({{bug(1422312)}})。

### JavaScript

変更なし。

### API

- 非標準の [IDBMutableFile](/ja/docs/Web/API/IDBMutableFile)、[IDBFileHandle](/ja/docs/Web/API/IDBFileHandle)、[IDBFileRequest](/ja/docs/Web/API/IDBFileRequest) インターフェイスおよび [IDBDatabase.createMutableFile()](/ja/docs/Web/API/IDBDatabase#idbdatabase.createmutablefile) メソッドを、将来のリリースで削除する準備としてデフォルトで無効にしました ({{bug(1764771)}})。

- [Transform streams](/ja/docs/Web/API/TransformStream) をサポートしました。{{domxref("ReadableStream")}} から {{domxref("WritableStream")}} へチャンクを運んで、変換処理を実行できます。
  この更新には新しい [`TransformStream`](/ja/docs/Web/API/TransformStream) および [`TransformStreamDefaultController`](/ja/docs/Web/API/TransformStreamDefaultController) インターフェイスと [`ReadableStream.pipeThrough()`](/ja/docs/Web/API/ReadableStream/pipeThrough) メソッドが含まれます ({{bug(1767507)}})。

- [読み取り可能なバイトストリーム](/ja/docs/Web/API/Streams_API#bytestream-related_interfaces) をサポートしました。基になるバイトソースからコンシューマーへ、データを効率的にゼロバイト転送できます (ストリームの内部キューをバイパスします)。
  サポートした新しいインターフェイスは {{domxref("ReadableStreamBYOBReader")}}、{{domxref("ReadableByteStreamController")}}、{{domxref("ReadableStreamBYOBRequest")}} です ({{bug(1767342)}})。

#### DOM

- Firefox 固有の {{domxref("Window.sidebar")}} プロパティを、設定で無効にしました。将来削除する予定です ({{bug(1768486)}})。

### WebDriver conformance

#### WebDriver BiDi

- Webdriver BiDi の `browsingContext.navigate` をいくつか改良しました。
  - ナビゲーションが誤ってタイムアウトする場合があるエッジケースを修正しました ({{bug(1766217)}})。
  - ハッシュの変更をサポートしました ({{bug(1763127)}})。
  - エラーページへのナビゲーションをサポートしました ({{bug(1763124)}})。

#### Marionette

- Marionette が、ウィンドウがない Firefox のインスタンスへ接続できるようになりました ({{bug(1726465)}})。
- ナビゲーションを開始する前に、PageLoadStrategy が "none" である `WebDriver:Navigate` が返る問題を修正しました ({{bug(1754132)}})。
- 別のタブへ切り替えるときに `WebDriver:SwitchToWindow` で競合状態が発生する可能性がある問題を修正しました ({{bug(1749666)}})。

## アドオン開発者向けの変更点一覧

- スクリプトの実行、CSS の挿入と削除、コンテンツスクリプトの登録管理の機能を提供する {{WebExtAPIRef("scripting")}} API が、Manifest V2 で利用可能になりました ({{bug(1766615)}})。
- Firefox で 'wasm-unsafe-eval' CSP キーワードをサポートしたことに伴って ({{bug(1740263)}})、Manifest V3 拡張機能で [WebAssembly](/ja/docs/WebAssembly) を使用するために [content_security_policy](/ja/docs/Mozilla/Add-ons/WebExtensions/manifest.json/content_security_policy) マニフェストキーで、このキーワードを指定することが必要になりました。後方互換性のため、Manifest V2 拡張機能は引き続きこのキーワードがなくても WebAssembly を使用できます ({{bug(1766027)}})。
- {{WebExtAPIRef("privacy.websites")}} の `cookieConfig` プロパティで、`nonPersistentCookies` オプションが非推奨になりました ({{bug(1754924)}})。

## 過去のバージョン

{{Firefox_for_developers(101)}}
