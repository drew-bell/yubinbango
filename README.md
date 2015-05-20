## Yubinbangoについて

これまでにない設定方法のまったく新しいライブラリが誕生いたしました！
このYubinBangoライブラリの革新的な設定方法は今は特殊に感じるかも知れませんが、おそらく10年以内にはこれが当たり前になっているはず。

## 背景

設置後の郵便番号データの更新作業から解放される革新的なライブラリajaxzip3の公開から8年。Google Codeの閉鎖の告知とともにGithubに移行しましたが、これを機に新しいコードベースに移行することに。さらに郵便番号データの更新をCircleCIで自動化いたしました。
新しいコードは基本機能のみを抽出したCoreモジュールと、これまでのajaxzip3と互換性を保つためのモジュール、さらにまったく新しいYubinBangoライブラリの3つのモジュールと、郵便番号データで構成されています。コードを見直すことによりさらに軽量化いたしました。郵便番号が全角数字で入力された場合は半角数字に自動変換します。ハイフンが入力されても動作します。

## YubinBangoの設定方法

今度の郵便番号検索ライブラリは、なんとclassを指定するだけ！
[microformats2](http://microformats.org/wiki/h-adr)の標準仕様に合わせたclassを記載をするだけで郵便番号検索機能が有効になります。

    <script src="https://yubinbango.github.io/yubinbango/yubinbango.js" charset="UTF-8"></script>
    <form class="h-adr">
      <span class="p-country-name" style="display:none;">Japan</span>

      〒<input type="text" class="p-postal-code" size="8" maxlength="8"><br>

      <input type="text" class="p-region p-locality p-street-address p-extended-address" /><br>
    </form>

## YubinBangoライブラリを有効にするには

YubinBangoが有効になる条件は下記の通りです。

1. scriptタグでYubinBangoライブラリが読み込まれていること
2. formタグのclass指定の中に h-adr が含まれていること
3. form中で、国名(p-country-name) が Japan に指定されていること
4. 郵便番号入力欄のclass指定の中に p-postal-code が含まれていること
5. 住所欄のclass指定の中に、都道府県名(p-region)、市町村区(p-locality)、町域(p-street-address)、以降の住所(p-extended-address) がそれぞれ含まれていること

## その他の設定方法

住所欄を分ける場合は下記のようにします。

    <form class="h-adr">
      <span class="p-country-name" style="display:none;">Japan</span>

      〒<input type="text" class="p-postal-code" size="3" maxlength="3">
      <input type="text" class="p-postal-code" size="4" maxlength="4"><br>

      <input type="text" class="p-region" readonly /><br>
      <input type="text" class="p-locality" readonly /><br>
      <input type="text" class="p-street-address" /><br>
      <input type="text" class="p-extended-address" />
    </form>