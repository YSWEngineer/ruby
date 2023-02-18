**<details><summary>#02 文字列を表示してみよう</summary>**
  - コメント方法

    ```ruby
    # 先頭にパウンド記号(#) コメント　で文末までコメント扱いになる。

    # comment
    ```

    ```ruby
    # 複数行のコメントの場合、=begin と =end の間に何行でも書いていくことができる。

    =begin
    comment
    comment
    =end
    ```

  - ターミナルについて

    ```ruby
    # ターミナル内をクリアにする

    % clear と打つか または control + L
    ```
</details>

**<details><summary>#03 変数を使ってみよう</summary>**
- 変数は値につける名前のこと。
- 変数に値を割り当てることを「値を代入する」というので、用語として覚えておいてください。
- 文字列の中に変数を埋め込むこともできます。
    - 変数を埋め込むには`#{}`で変数名を`#{name}`と書いてあげる。
- 変数を使うとプログラムが変更に強くなるという利点があります。
    - 例えばyoshiwoを大文字にしたかった場合、変数を使っていなかったらyoshiwoと書いていた箇所全てを修正する必要があります。ただし、変数を使えばname = “yoshiwo”の1箇所だけを直すだけで済むことがわかります。
    
    ```ruby
    # puts "hello yoshiwo"
    # puts "hello yoshiwo again!"
    
    name = "YOSHIWO"
    puts name
    
    puts "hello #{name}"
    puts "hello #{name} again!"
    ```
    
- 変数はとても便利なので、積極的に使っていくといいかと思います。</details>

**<details><summary>#04 ユーザーからの入力を受け取ろう</summary>**
