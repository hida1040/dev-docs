# スニペット

本項ではアプリケーションで採用可能な JavaScript Snippet を記述します。

## Debounce

### 説明
Debounce は、特定の間隔内で連続して発生する操作（イベント）を破棄し、それらを1回の呼び出しに統合します。  
Window のリサイズや、キー入力等の高頻度にトリガーされるイベントや、  
ユーザー操作によってトリガーされる（意図しない）連続的な処理実行を制御するためのテクニックです。  

Debounce には、以下のようなメリットがあります。  
- **パフォーマンスの向上**
  不要な関数の実行を抑制し、アプリケーションのパフォーマンスを向上させる。
- **APIコストの削減**
  不要なAPIリクエストを抑制し、リクエスト回数を削減する。
- **ユーザーエクスペリエンスの向上**
  不要な動作や画面上のアニメーション等を適切に表示し、効果的なユーザーエクスペリエンスを提供する。

具体的には、Debounce は以下のような動作上の課題を解決します。
- ユーザー操作によって同内容の Submit 処理が複数回実行されてしまった
- キー入力のたびにAPIが呼び出され、パフォーマンス上の懸念がある

see: [MDN - Debounce](https://developer.mozilla.org/en-US/docs/Glossary/Debounce)

### function

```javascript
    /**
    * debounce()
    * 渡された関数の新しいデバウンスバージョンを作成して返します。
    * この関数は、最後に呼び出されてから waitミリ秒が経過するまで実行を延期します。
    * 入力が到着しなくなった後にのみ発生する動作を実装するのに役立ちます。
    * 即時引数 にtrue を 渡すと、 debounce は待機間隔の終了時ではなく終了時に関数をトリガーします。
    * これは、「送信」ボタンを誤ってダブルクリックして 2 度目に実行されるのを防ぐ場合などに便利です。
    * @param {Function} func Function
    * @param {Number} wait 待機間隔(ミリ秒)
    * @param {Boolean} immediate 即時引数
    * @returns 
    */
    function debounce(func, wait, immediate) {
        var timeout;
        return function() {
                var context = this, args = arguments;
                clearTimeout(timeout);
                timeout = setTimeout(function() {
                        timeout = null;
                        if (!immediate) func.apply(context, args);
                }, wait);
                if (immediate && !timeout) func.apply(context, args);
        };
    };
```

### 使用例

Input へのキー入力時（liveChange）のイベントに対する Debounce の使用例です。
`debounce()` の第一引数に適用したい function を 記述します。  
`debounce()` の第二引数に遅延させたい数値を設定します。（ミリ秒）  
以下の例では、function onChangeInput が 0.5 秒の間に複数回呼び出されても、1回の処理実行に統合します。  

```javaScript
    onChangeInput: debounce(function (oEvent) {
    ....
    }, 500),
```

