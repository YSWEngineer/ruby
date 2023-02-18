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
- 入力を受け取って変数に代入してみましょう。
    - gets(ゲッツ、ゲットエス)という命令を使えば、入力を受け取って返してくれるので、`name = gets` としてあげます。
    - puts(プッツ、プットエス)。
    
    ```ruby
    % ruby main.rb
    tom
    hello tom
    hello tom
     again!
    ```
    
    - again!の手前で変な改行が入っているのが気になります。これは、getsは改行付きで値を取得するからなので、改行を除去したい場合は`gets.chomp`(チョンプ)としてあげればOKです。
    
    ```ruby
    name = gets.chomp # 改行を除去する
    
    puts "hello #{name}"
    puts "hello #{name} again!"
    ```
    
    ```ruby
    % ruby main.rb
    tom
    hello tom
    hello tom again!
    ```
    
    - 入力待ちをする時にメッセージがあるとわかりやすいので、getsの前にYour name?と常時して訊くようにしてあげましょう。
    
    ```ruby
    puts "Your name?"
    name = gets.chomp
    
    puts "hello #{name}"
    puts "hello #{name} again!"
    ```
    
    ```ruby
    % ruby main.rb
    Your name?
    ```
    
    - 表示がされましたが、Your name?のあとに改行がない方がわかりやすいですね。
    - では、プログラムを一旦終了させたいのですが、オンラインターミナルを1回クリックしてアクティブにした後に、プログラムを途中で止めるにはcontrol + C としてあげればOKです。
    
    ```ruby
    # control + C を実行 変なメッセージが出ますが、プロンプトに戻っていればOKです
    % ruby main.rb
    Your name?
    ^Cmain.rb:2:in `gets': Interrupt
    	from main.rb:2:in `gets'
    	from main.rb:2:in `<main>'
    
    yoshiwo@Yoshiwos-MacBook-Pro dotinstall.ruby %
    ```
    
    - 修正をどのようにするのかというと、1行目のputsをprintにしてあげれば、最後に改行が出力されないのでこれで実行してみます。
    - プロンプトとは`~ %`の部分です。これが出ているときは、Linuxコマンドが入力できる状態であることを表しています。
    
    ```ruby
    print "Your name?"
    name = gets.chomp
    
    puts "hello #{name}"
    puts "hello #{name} again!"
    ```
    
    ```ruby
    % ruby main.rb
    Your name? tom
    hello  tom
    hello  tom again!
    ```
    
- まとめ
  - gets
  - chomp
  - プログラムの終了方法(ターミナル)</details>
  
**<details><summary>#05 数値を受け取って計算してみよう</summary>**
- 今回作りたいのは数当てゲームなので、数を受け取って何らかの計算をとりあえずしてみましょう。
    - 今までの復習になりますが、改行なしでメッセージを表示したいのでprint “Your number?”としてあげつつ、入力を受け取ってnumに入れてあげましょう。
    - numを表示したいのですが、その時に計算をしてあげましょう。入力した数値に3を足して出力してみます。
    - 実行して、適当に数字を入力してreturnを押すと、エラーになります。
    
    ```ruby
    % ruby main.rb
    Your number? 5 # 5を入力して、returnを押すとエラーが表示
    main.rb:4:in `+': no implicit conversion of Integer into String (TypeError)
    	from main.rb:4:in `<main>'
    ```
    
    - これはgetsが受け取るのは、あくまでも文字列だからです。したがって、計算するために数値に変換するための処理が必要です。
    - いろいろな方法がありますが、chompを`.to_i`にすると整数値に変換してくれます。このto_iはto integerの略です。
    - なお、整数値に変換するとそもそも改行がなくなるので、さらにchompする必要はありません。
    
    ```ruby
    print "Your number?"
    num = gets.to_i
    
    puts num + 3
    ```
    
    ```ruby
    % ruby main.rb
    Your number? 5
    8
    ```

- 要点まとめ
  - 数値への変換
  - 動作確認</details>

- #06 条件に応じて表示を変えよう
