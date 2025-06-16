# プログラミング課題（括弧の対応判定）
# 使用言語
- javaScript

## 課題内容

小括弧 `()`, 中括弧 `{}`, 大括弧 `[]` のみで構成された文字列 `s` が与えられたとき、以下のルールに従っているかを判定するプログラムを作成してください。

### ルール

1. 開き括弧 `({[` は、同じ種類の閉じ括弧 `)}]` で閉じること。
2. 括弧を開いた順に括弧を閉じること

## 実行例
- 例１
 入力：s="()"
 出力：true
- 例２
 入力：s="([]){}"
 出力：true
- 例３
 入力：s="({)}"
 出力：false

# 回答のコード
```javascript
const isValid = (s) => {
    // ここにコードを書いてください
    // 同じ括弧の種類を対応させておく
    const documents = {
        ')': '(',
        ']': '[',
        '}': '{',
    }
    const place = [];

    for (let check of s) {
        // 括弧以外の文字があったら false
        if (check !== "(" && check !== "{" && check !== "[" && check !== ")" && check !== "}" && check !== "]") {
            return false;
        }
        // 開き括弧は配列にpush
        else if (check === "(" || check === "{" || check === "[") {
            place.push(check);
        }
        // 閉じ括弧が渡ってきたら、配列の一番後ろを切り取りそれが渡ってきた閉じ括弧と同じ種類か確認
        else {
            if (place.pop() !== documents[check]) {
                return false;
            }

        }
    }
    //placeが空配列だったらOK
    if (place.length === 0) {
        return true;
    }
    //空配列じゃなかったらダメ
    else {
        return false;
    }
};
