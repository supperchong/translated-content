---
title: HTMLMediaElement.load()
slug: Web/API/HTMLMediaElement/load
page-type: web-api-instance-method
tags:
  - API
  - Audio
  - Element
  - HTML DOM
  - HTMLMediaElement
  - Media
  - Method
  - Reference
  - Video
  - load
  - reset
browser-compat: api.HTMLMediaElement.load
translation_of: Web/API/HTMLMediaElement/load
---
{{APIRef("HTML DOM")}}

{{domxref("HTMLMediaElement")}} の **`load()`** メソッドは、メディア要素をその初期状態にリセットし、再生を開始する準備としてメディアソースを選択してメディアを読み込むプロセスを開始します。

先読みされるメディアデータの量は、要素の {{htmlattrxref("preload", "video")}} 属性の値によって決まります。

このメソッドは通常、要素の {{htmlattrxref("src", "video")}} 属性を変更するか、メディア要素自体の中にネストされている {{HTMLElement("source")}} 要素を追加または削除することによって、メディア要素に使用可能な一連のソースを動的に変更した場合にのみ役立ちます。 `load()` は要素をリセットして利用可能なソースを再スキャンし、それによって変更を有効にします。

## 構文

```js
load()
```

### 引数

なし。

### 返値

なし ({{jsxref("undefined")}})。

## 使用上のメモ

`load()` を呼び出すと、このメディア要素を含む進行中のすべての操作が中止され、{{HTMLElement("audio")}} 要素または {{HTMLElement("video")}} 要素で指定されたオプションとその {{htmlattrxref("src", "video")}} 属性または子の {{HTMLElement("source")}} 要素を指定して適切なメディアリソースの選択と読み込みのプロセスが開始されます。 これについては、[動画と音声のコンテンツ](/ja/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)の[複数の形式の対応](/ja/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content#supporting_multiple_formats)で詳しく説明しています。

進行中のアクティビティを中止するプロセスにより、 {{domxref("HTMLMediaElement.play", "play()")}} によって返された未処理のプロミス ({{jsxref("Promise")}}) が、新しいメディアの読み込みが開始される前に、そのステータスに基づいて適切に解決または拒否されます。保留中の再生用のプロミスは、 `"AbortError"` {{domxref("DOMException")}} で中止されます。

読み込みプロセスが進むにつれて、次のように適切なイベントがメディア要素自体に送信されます。

- 要素がすでにメディアの読み込み処理中の場合、その読み込み処理は中止され、 **{{domxref("HTMLMediaElement/abort_event", "abort")}}** イベントが送信されます。
- 要素がすでにメディアで初期化されている場合は、 **{{domxref("HTMLMediaElement/emptied_event", "emptied")}}** イベントが送信されます。
- 再生位置をメディアの先頭にリセットすると、実際に再生位置が変更された場合（つまり、まだ先頭になっていない場合）、 **{{domxref("HTMLMediaElement/timeupdate_event", "timeupdate")}}** イベントが送信されます。
- メディアが選択され、読み込みの開始準備が整うと、 **{{domxref("HTMLMediaElement/loadstart_event", "loadstart")}}** イベントが配信されます。
- これ以降は、メディアの読み込みと同じようにイベントが送信されます。

## 例

この例では、文書内の {{HTMLElement("video")}} 要素を見つけて、`load()` を呼び出してそれをリセットします。

```js
var mediaElem = document.querySelector("video");
mediaElem.load();
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
