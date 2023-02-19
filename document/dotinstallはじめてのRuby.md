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
    
- 要点まとめ
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

**<details><summary>#06 条件に応じて表示を変えよう</summary>**
- 次は、受け取った数値があらかじめ用意しておいた答えと一致するかどうかを調べて、結果を表示してみましょう。
    - answerという変数を用意してあげて、今回は答えは6としましょう。
    - それからメッセージは、「数を当てる」という意味で、推測を意味するguessにしておきます。また、変数名もguessにしておくとわかりやすいです。
    
    ```ruby
    answer = 6
    
    print "Your guess?"
    guess = gets.to_i
    ```
    
    - answerとguessを比べたいのですがif endという命令を使ってあげます。なお、answerとguessが等しいという記号は==を使ってあげてください。変数に値を代入するのが`=`、比較する時に使うのが`==`なので、間違えないようにしてください。
    - もし等しかった時の処理はifとendの間に書けばよいのでBingo!と表示してあげましょう。
    
    ```ruby
    answer = 6
    
    print "Your guess?"
    guess = gets.to_i
    
    if answer == guess
      puts "Bingo!"
    end
    ```
    
    ```ruby
    % ruby main.rb
    Your guess? 6
    Bingo!
    
    % ruby main.rb
    Your guess? 3
    ```
    
    - 数字が合えばBingo!が表示されます。もしanswerとguessが等しくなかった場合にもメッセージを出したい場合は、間にelseと書いてあげて、endの間にanswerとguessが等しくなかった時の処理を書いてあげればOKです。
    
    ```ruby
    answer = 6
    
    print "Your guess?"
    guess = gets.to_i
    
    if answer == guess
      puts "Bingo!"
    else
      puts "Boo..."
    end
    ```
    
    ```ruby
    % ruby main.rb
    Your guess? 3
    Boo...
    ```
    
    - ちゃんとBoo...と出たのがわかります。
- 要点まとめ
  - if...end
  - if...else...end</details>

**<details><summary>#07 条件を追加してみよう</summary>**
- 次は、answerとguessを比べてanswerがもっと大きいのか、もっと小さいのかも表示してみましょう。どうするかというと、さらに条件を加えてあげればいいですね。
  - elsifとして条件を書きます。
  - answerがguessより大きかったら、もっと大きな数字だよ、という意味でBigger!と表示してあげましょう。
  - それから、どちらの条件にも当てはまらなかったら、それはanswerがguessより小さいということなので、もっと小さな数字だよ、という意味でSmaller!と表示してあげます。

  ```ruby
  answer = 6

  print "Your guess?"
  guess = gets.to_i

  if answer == guess
    puts "Bingo!"
  elsif answer > guess
    puts "Bigger!"
  else
    puts "Smaller!"
  end
  ```

  ```ruby
  % ruby main.rb
  Your guess? 5
  Bigger! # 答えが6なのでbigger!が表示

  % ruby main.rb
  Your guess? 8
  Smaller! # 答えが6なのでSmaller!が表示

  % ruby main.rb
  Your guess? 6
  Bingo! # 答えが6なのでBingo!が表示
  ```

  - 答えが決まっているのもつまらないので、answerがランダムに決まるようにしてあげましょう。どうするかというと、rand()という命令を使ってあげます。
  - `rand(10)`とすると、0から10未満のランダムな整数値を生成してくれるので0から9のどれかになります。
  - 今回欲しいのは1から10なので + 1してあげればよいでしょう。
  - ついでに正解も表示するようにしてみましょう。判定が終わった後に、「答えはこれだったよ」とputsで変数を埋め込みながら表示してあげます。

  ```ruby
  answer = rand(10) + 1

  print "Your guess?"
  guess = gets.to_i

  if answer == guess
    puts "Bingo!"
  elsif answer > guess
    puts "Bigger!"
  else
    puts "Smaller!"
  end

  puts "Answer was #{answer}"
  ```

  ```ruby
  % ruby main.rb
  Your guess? 6
  Bigger!
  Answer was 9

  % ruby main.rb
  Your guess? 9
  Smaller!
  Answer was 5
  ```

  - こうした乱数も使えるようになっておきましょう。
- 要点まとめ
  - if...elsif...else...end
  - 乱数</details>

**<details><summary>#08 ループ処理を使ってみよう</summary>**
- 次は、正解するまで何回もチャレンジできるようにしてみましょう。
    - どうするかというとループ処理で囲ってあげます。
    - loop do endとしてあげて、数を当てる処理をカットして、貼り付けてあげればよいでしょう。
    - 字下げが崩れた場合は、範囲選択してtabキーでなおすことができるので覚えておいてください。
    
    ```ruby
    answer = rand(10) + 1
    
    loop do
      print "Your guess?"
      guess = gets.to_i
    
      if answer == guess
        puts "Bingo!"
      elsif answer > guess
        puts "Bigger!"
      else
        puts "Smaller!"
      end
    
      puts "Answer was #{answer}"
    end
    ```
    
    - ただ、このままだと永久にループしてしますので、条件に合致したらループから抜けてあげましょう。answerがguessと一緒だった場合に終わりたいので、breakとしてあげるとループを抜けることができます。
    - それから、正解を表示してはゲームにならないので、puts “Answer was #{answer}”は消してあげましょう。
    
    ```ruby
    answer = rand(10) + 1
    
    loop do
      print "Your guess?"
      guess = gets.to_i
    
      if answer == guess
        puts "Bingo!"
        break
      elsif answer > guess
        puts "Bigger!"
      else
        puts "Smaller!"
      end
    end
    ```
    
    ```ruby
    % ruby main.rb
    Your guess? 6
    Smaller!
    Your guess? 5
    Bingo!
    % 
    ```
    
    - Bingo!になってループを抜けて終了したのがわかります。
    - こうしたループ処理もプログラミングではよく使うので慣れておくようにしてください。</details>

