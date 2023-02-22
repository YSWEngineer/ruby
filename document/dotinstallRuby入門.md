# 💻dotinstall Ruby入門
**<details><summary>#01 Rubyを使ってみよう</summary>**
- 今回は、概要と公式サイト、レッスンにおいて必要となる知識、レッスンにおける環境についてみていきたいと思います。
    - 概要
        - Rubyはオブジェクト指向のスクリプト言語になります。
        - Webサービスを比較的簡単に作れるRuby on Railsを採用。
    - 公式サイト [ruby-lang.org](http://ruby-lang.org)
    - 知識
        - ローカル開発環境の構築
            - CentOS6終了につきサポート終了したため、Cloud9(クレジットカード必須)を利用するか、『はじめてのRuby』で使われている実行環境を使うのがよいでしょう。
            - ここでいう実行環境はmacOSの場合、ターミナルでも補えると推測。
                - ①ドットインストールのレッスン動画
                - ②macOSのターミナル
                - ③必要に応じてフォルダ、ファイルの作成
                - ターミナルが利用不可ならドットインストールの実行環境を利用すればよい。最後の手段として取っておこう。
        - Cloud9入門 ※クレジットカード必須→利用不可
        - UNIXコマンド入門
            - Ruby入門と平行して学習しよう。
    - 環境
        - ローカル開発環境(ターミナルを使用)
        - フォルダはdotinstall.ruby
        - irb
            - これを使うと、インタラクティブにRubyを操作していくことができます。コードの見通しが悪くなりますが、少し何かを試したいという場合には便利なので知っておくといいでしょう。
            - 「irb」打つとコマンドラインで命令が打てるので、ここで試して実行結果を確認することができます。
            
            ```ruby
            % irb
            irb(main):001:0> p "hello"
            "hello"
            => "hello"                                       
            irb(main):002:0>
            ```
            
            - 抜けるときは「exit」。
            
            ```ruby
            % irb
            irb(main):001:0> p "hello"
            "hello"
            => "hello"                                       
            irb(main):002:0> exit
            yoshiwo@Yoshiwos-MacBook-Pro ruby_lessons %
            ```
            
            - インタラクティブ
                - **①**相互に作用するさま。
                - **②**情報の送り手と受け手が相互に情報をやりとりできる状態。現在のコンピューターによる情報処理の形式。対話型。
        - ri
            - このコマンドを使うと、知りたい命令やオブジェクトのドキュメントを見ることができます。例えば「ri Array」としてあげるとArrayオブジェクトに関する情報が出てきます。
            
            ```ruby
            = Array < Object
            
            ------------------------------------------------------------------------
            = Includes:
            Enumerable (from ruby core)
            
            (from ruby core)
            ------------------------------------------------------------------------
            An Array is an ordered, integer-indexed collection of objects, called
            elements.  Any object may be an Array element.
            ……続く
            ```
            
            - 英語になっていますが、例も豊富なので何かわからないことがあった時に調べてみるのもいいかと思います。
            - 「q」キーで押すと抜けることができます。</details>

**<details><summary>#02 はじめてのRubyプログラム</summary>**
- お約束ではありますが、hello worldと表示させてみます。
    - とは言っても簡単で、(エディターに)print “hello world”と書いてあげればいいです。
    
    ```ruby
    print "hello world"
    ```
    
    - 実行には(ターミナルで)rubyコマンドを使ってあげて、ファイル名を渡してあげればOKです。
    
    ```ruby
    % ruby hello.rb
    hello world
    ```
    
    - printは渡したオブジェクトを文字列にして表示させるための命令になります。
    - ダブルクォーテーション(””)は文字列を表現するための記法なので覚えておきましょう。
    - 今は1行しかプログラムがありませんが、複数行書いた場合は基本的に上から実行されていきます。
    - 命令の区切りにはセミコロン(;)も使えたりするのですが、改行があれば省略できるので、1行に複数の命令を書きたい時くらいしか使わないということも覚えておきましょう。
    - コメントの書き方は、パウンド記号(#)の後がコメントになるので、動作に影響を与えないメモ書きを書いておくのに便利かと思います。
    - また、複数行一気にコメントにしたい場合には、=beginと=endで囲ってあげましょう。そうすることで動作に関係ない埋め込みドキュメントとして認識されるので、こちらを使ってもいいかと思います。
    - printと似たような命令で、putsとpがあるので、そちらもついでに勉強しておきましょう。
    - putsはprintと似たような動作をするのですが、改行が付くという特徴があります。
    - pは、主にデバッグ用に使われます。オブジェクトの種類がわかりやすいように表示してくれる命令です。なので、単にhello worldだけでなくて、これは文字列だよと分かりやすいように、ダブルクォーテーションで囲われて表示されています。
    
    ```ruby
    # コメント
    
    =begin
    コメント
    コメント
    コメント
    コメント
    =end
    
    print "hello world"
    puts "hello world" # +改行
    p "hello world" # デバッグ用
    ```

-　要点まとめ
    - はじめてのRubyプログラム
    - プログラムの実行
    - コメント
    - print, puts, p</details>

**<details><summary>#03 変数、定数を使ってみよう</summary>**
- 変数について。
    - 変数はデータにつけるラベルのようのものです。変数を使うことで、複雑なデータにわかりやすい名前をつけたり、その名前で計算や使い回しができたりするので見ていきましょう。
    - シンプルな例ですが、前回のプログラムを変数を使って書き換えてみたいとも思います。
        - hello worldという値にmsgという変数を割り当ててあげましょう。msgはmessageの省略形。
        - 変数にはルールがあって、英小文字もしくはアンダーバー(_)で始めないといけないというルールがあります。
        - 変数には何回でも値を割り当てることができます。例えば、msg = “hello world again’のように、あとで値を書き換えて再度表示してみると、今度はputs msgではhello world againが表示されます。
        
        ```ruby
        # 変数
        # 変数名は 英小文字 または _ から始める
        
        msg = "hello world"
        puts msg
        
        msg = "hello world again"
        puts msg
        ```
        
        ```ruby
        % ruby hello.rb
        hello world
        hello world again
        ```
        
        - 変数は実はもう少し奥が深いのですが、まずは基本としてこの辺りを押さえておいてください。
- 定数について。
    - 定数も変数と同じで値に付けるラベルなのですが、変数と違ってプログラム中で値を書き換えて欲しくないものに対して使います。
    - 定数の名前の付け方にもルールがあり、最初が英小文字でないといけません。
    - 慣習的に全部大文字にすることが多いです。
    - 定数を書き換えるとおかしなことになりますので、見てみましょう。
    
    ```ruby
    # 変数
    # 変数名は 英小文字 または _ から始める
    
    # msg = "hello world"
    # puts msg
    
    # msg = "hello world again"
    # puts msg
    
    # 定数
    # - 英大文字
    
    VERSION = 1.1
    puts VERSION
    
    VERSION = 1.2
    puts VERSION
    ```
    
    ```ruby
    % ruby hello.rb
    1.1
    hello.rb:16: warning: already initialized constant VERSION
    hello.rb:13: warning: previous definition of VERSION was here
    1.2
    ```
    
    - 最初に1.1と表示されるのですが、その後に警告が出ているのがわかります。Rubyでは警告は出してくれますが、そこで処理が止まるわけではなく、実際にはこのように値が書き変わって表示されてしまうので、その点に注意しつつ、警告を無視せずにきちんと対処するようにしておいてください。
- 要点まとめ
    - 変数
    - 定数</details>

**<details><summary>#04 オブジェクトを理解しよう</summary>**
- 用語について整理しておきましょう
    - まず大事なのは、Rubyではすべての値がオブジェクトになっているという点です。
    - 前回の例で言うと、"hello world”や1.1が値なので、これらはオブジェクトという意味ですね。
    - オブジェクトは何かということですが、この時点では便利な命令をいろいろ持っているデータ型だと思っておいてください。
    - 例えば”hello world”は、これはオブジェクトなので、後ろに付けられる便利な命令がいろいろ用意されていて、.lengthを付ければ文字数を返してくれます。また、.reverseという命令をつけてあげると、文字列を逆順にした文字列を返します。
    - 1.1についても同じで、こちらもオブジェクトなので、.roundという命令を付けてあげると四捨五入して1を返します。.floorという命令を付けてあげると小数点以下を切り捨ててくれるので、こちらも1を返します。
    - Rubyではこうした便利な命令をオブジェクトの種類によってたくさん用意していて、その命令のことをMethod(メソッド)と呼ぶので、用語として覚えておいてください。
    - どのメソッドが使えるかは、その値がどの種類のオブジェクトに属しているかによって変わってきます。
    - そのオブジェクトの種類のことをクラスと言って、Rubyは文字列に関するStringクラス、1.1のような浮動小数点数の場合はFloatクラスと、たくさんのクラスが用意されています。
    - Rubyではこれらのクラスの扱いに慣れていくことで、思った通りのプログラミングができるようになっていきます。
    - オブジェクトの種類はクラスと言うのですが、1.1や”hello world”などの実際の値のことはインスタンスと呼ぶので、用語として覚えておいてください。
- 要点まとめ
    - オブジェクト
    - クラス
    - メソッド
    - インスタンス</details>

**<details><summary>#05 数値オブジェクトを使おう</summary>**
- 数値に関するオブジェクトについて、もう少し詳しく見ていきましょう。
    - 表現方法は、32や4.8といった具合に書いていけばOKです。
    - オブジェクトがどのクラスに属していて、どのようなメソッドを持っているかを調べる方法について見ていきましょう。
        - とは言っても簡単で、.classメソッド、.methodsメソッドを使えばOKです。
        
        ```ruby
        # 数値
        # 32 4.8
        
        p 4.8.class
        p 4.8.methods
        ```
        
        ```ruby
        % ruby hello.rb
        Float # クラスの種類
        [:zero?, :angle, :**, :<=>, :-@, :phase, :<=, :>=, :==, :===, :nan?,
         :infinite?, :finite?, :next_float, :prev_float, :eql?, :%, :*, :+,
         :inspect, :-, :/, :<, :>, :to_int, :to_s, :to_i, :to_f, :to_r, :divmod,
         :fdiv, :quo, :coerce, :modulo, :numerator, :denominator, :rationalize,
         :magnitude, :abs, :floor, :ceil, :arg, :round, :truncate, :positive?,
         :negative?, :hash, :polar, :dup, :imaginary, :imag, :+@, :to_c, :abs2,
         :real, :conjugate, :conj, :real?, :singleton_method_added, :div, :integer?,
         :clone, :i, :remainder, :nonzero?, :step, :rectangular, :rect, :between?,
         :clamp, :singleton_class, :itself, :taint, :tainted?, :untaint, :untrust,
         :untrusted?, :trust, :methods, :singleton_methods, :protected_methods,
         :private_methods, :public_methods, :instance_variables, :instance_variable_get,
         :instance_variable_set, :instance_variable_defined?, :remove_instance_variable,
         :instance_of?, :kind_of?, :is_a?, :display, :public_send, :class, :frozen?,
         :then, :tap, :yield_self, :extend, :method, :public_method, :singleton_method,
         :define_singleton_method, :=~, :!~, :nil?, :respond_to?, :freeze, :object_id,
         :send, :to_enum, :enum_for, :__send__, :!, :instance_eval, :instance_exec,
         :!=, :equal?, :__id__] # メソッドの紹介
        ```
        
        - たくさん出てきましたが、4.8はFloatクラスで、メソッドはこういったものがあるよ、というのがわかります。
        - **や=~などの記号もメソッドであることに注意しておいてください。
- 代表的なメソッドについて。
    - 四則演算
        - 足し算 は +、引き算は -、掛け算は *、割り算は /を使えばOKです。
        - 余りについては %、べき乗は **を使います。
            - 例を見ていきましょう。
            
            ```ruby
            # 数値
            # 32 4.8
            
            # p 4.8.class
            # p 4.8.methods
            
            # + - * / % **
            
            p 10 + 3
            p 10 * 3
            p 2.4 * 2 # 浮動小数点数についてもつかえるのでこのような書き方もできます。
            p 10 / 3 # 3 商は普通に/にする。
            p 10 % 3 # 1 余りの場合は%にする。
            p 10.0 / 3 # 10割る3を3.33333...にしたい場合は、どちらかを浮動小数点数にしてあげればよいので、「10.0 / 3」とすればOKです。
            p Rational(2, 5) + Rational(3, 4) #Rubyでは有理数(分数)の扱いもできて、その場合はRationalを使ってあげてください。
            # 例えば、2 / 5を表現したい場合には「Rational(2, 5)」と書けばOKです。
            # 分数同士の計算もできるので「5分の2足す4分の3」の場合は「Rational(2, 5) + Rational(3, 4)」と書きます。
            p 2/5r + 3/4r # Rationalは短い書き方が用意されていて、5分の2の場合は「2/5r」と書きます。
            ```
            
            ```ruby
            % ruby hello.rb
            13
            30
            4.8
            3
            1
            3.3333333333333335
            (23/20)
            (23/20)
            ```
            
        - Floatクラスに関しては、前回も言いましたが、四捨五入や小数点以下の切り捨て切り上げなどができたりします。
            - どういうメソッドを使うかというと、四捨五入の場合はround、そして小数点以下切り捨ての場合はfloor、小数点以下の切り上げの場合はceil(シール)という命令を使ってあげてください。
            
            ```ruby
            p 52.6.round #四捨五入
            p 52.6.floor # 小数点以下切り捨て
            p 52.6.ceil # 小数点以下切り上げ
            ```
            
            ```ruby
            % ruby hello.rb
            53
            52
            53
            ```
            
        - 質問:小数点の掛け算がキリの悪い数値になるのは何故ですか？
            - 先生:実はコンピュータは数値を2進数で扱っていますので、10進数で表している数値をそのまま扱うことができません。特に小数点の扱いは限りなく近い数値という形でしか表現できず、今回もそれが原因でキリの悪い数値が出力されてしまっているのかなと思います。
- 要点まとめ
    - .class、.methods
    - 演算方法
    - 便利なメソッド</details>

**<details><summary>#06 文字列オブジェクトを使おう</summary>**
- 文字列オブジェクトについて。
    - 文字列はダブルクォーテーションで囲ってあげればOKです。もしくはシングルクォーテーションで囲っても文字列オブジェクトになるので、覚えておいてください。
    - ただ両者には違いがあって、ダブルヲーテーションの場合は特殊文字が使える、式展開ができる、という特徴があったりします。
        - 例えば”hello world”という文字列オブジェクトがあって、その中で改行やタブを表現したかった場合。
            - ダブルクォーテーションの中だったら\nで改行、\tでタブを表現することができます。
            - 同じことをシングルクォーテーションでやろうとすると改行やタブになりません。
            - 改行やタブ以外にも特殊文字はあるのですが、よく使うのはこの辺りかと思います。
            
            ```ruby
            # 文字列
            # "" 特殊文字 式展開
            # ''
            
            puts "hell\no worl\td"
            puts 'hell\no worl\td'
            ```
            
            ```ruby
            % ruby hello.rb
            hell
            o worl	d
            hell\no worl\td
            ```
            
            - シングルクォーテーションで囲った方に関しては、\nや\tがそのまま表示されているのでこういった違いがあるということを先ずは覚えておいてください。
    - 式展開についても例を出していきましょう。
        - 例えばpriceという文字列を書いたあとに#{}と書いてあげます。
        - #{}の中は、Rubyの式が評価されてそのまま表示されるので、例えば#{3000 * 4}としてあげると掛け算した結果がpriceの後に続けて表示されるはずです。シングルクォーテーションだとそのような展開はされないので、単に#{3000 * 4}とそのまま出てくるはずです。
        
        ```ruby
        puts "price #{3000 * 4}"
        puts 'price #{3000 * 4}'
        ```
        
        ```ruby
        % ruby hello.rb
        price 12000
        price #{3000 * 4}
        ```
        
        - このように式展開もできると覚えておいてください。
        - 当然、整数などを展開することもできるので、変数nameがあり文字列の中でnameを展開したい場合には”hello #{name}”としてあげてください。
        
        ```ruby
        name = "yoshiwo"
        puts "hello #{name}"
        ```
        
        ```ruby
        % ruby hello.rb
        hello yoshiwo
        ```
        
    - 文字列オブジェクトでよく使うメソッドについて。
        - + が連結、* が繰り返し。
        
        ```ruby
        # + 連結 * 繰り返し
        puts "hello" + "world"
        puts "hello" * 10
        ```
        
        ```ruby
        % ruby hello.rb
        helloworld
        hellohellohellohellohellohellohellohellohellohello
        ```

- 要点まとめ
    - 文字列の表現方法
    - 特殊文字
    - 式展開
    - 文字列の演算</details>

**<details><summary>#07 ?や!がついたメソッドを使おう</summary>**
- Rubyのメソッドでよく見掛けることになる!、?が付いたメソッドについての説明。
    - 例えば文字列を大文字にするためのメソッド、upcase。よくにたメソッドでupcase!があります。この2つの違いは、upcaseは文字列を大文字にしたものを返すだけ、upcase!は文字列を大文字にしたものを返しつつ、元の文字列も大文字に書き換えるという違いがあります。こうした!が付いたメソッドを大元のオブジェクトを書き換えてしまうという意味で、「破壊的なメソッド」と呼ぶので、覚えておいてください。
    
    ```ruby
    # !
    # - upcase
    # - upcase! 破壊的なメソッド
    
    name = "yoshiwo"
    puts name.upcase # 文字列を大文字にしたものを返すだけ
    puts name
    puts name.upcase! # 文字列を大文字にしたものを返しつつ、元の文字列も大文字に書き換えてしまう
    puts name
    ```
    
    ```ruby
    % ruby hello.rb
    YOSHIWO
    yoshiwo
    YOSHIWO
    YOSHIWO
    ```
    
    - 他にも全て小文字にするためのdowncaseや、文字順を逆にするためのreverseなどいろいろあるので、興味のある人は調べておいてください。
    - ?が付くメソッドは、真偽値を返すメソッドです。真偽値はtrueまたはfalseですが、条件判定や論理演算に使われるので、こういったメソッドにも慣れておきましょう。
    - 例えば文字列オブジェクトが空かどうかを調べるメソッドがあって、その場合はname.empty?と使ってあげてください。このような判定をすることで、ユーザーから入力された名前が空だったら何か別の名前にするといった処理も可能になります。
    - 他にも特定の文字が含まれているかどうかを調べるinclude?メソッドは、こちらも?が付いているので真偽値を返します。例えば、gが含まれているかどうか調べてみましょう。含まれていればtrue、含まれていなければfalseを返します。こういったメソッドにも慣れておいてください。
    
    ```ruby
    # ? 真偽値 true false
    
    name = "yoshiwo"
    p name.empty? # 文字列オブジェクトが空かどうかを調べる
    p name.include?("g") #特定の文字(今回は小文字の「g」)が含まれているかどうかを調べる
    ```
    
    ```ruby
    % ruby hello.rb
    false
    false
    ```

- 要点まとめ
    - 破壊的メソッド
    - 真偽値を返すメソッド</details>

**<details><summary>#08 配列オブジェクトを使おう</summary>**
- 複数のオブジェクトをまとめることができる配列オブジェクトについて見ていきましょう。
    - 例えばいろいろな色の名前をcolorsという変数にまとめたかったとします。
        - 配列の作り方なのですが、[ ]大括弧の中にそれぞれの要素を書いていってあげればOKです。文字列や文字列に数値を混ぜたり、配列の中に配列を入れることもできるので、覚えておいてください。
        - 要素へのアクセスの仕方は、最初の要素にはcolors[0]、次の要素にはcolors[1]、その次の要素にはcolors[2]......といった具合にアクセスできるので覚えておいてください。
        - [ ] 大括弧の中の数値を添字(そえじ)と言うので、これも覚えておいてください。
        - 添字はマイナスの値も指定することができます。colors[-1]は末尾、colors[-2]は末尾の1つ前......とアクセスできるので覚えておきましょう。
        - 範囲を指定することもできます。colors[0..2]とすると、color[0]からcolors[2]までを引っ張ってくれます。
        - もう1つ似たような書き方に、.を1つ増やしたcolors[0...2]があります。これは0から2の直前までになるので、これも覚えておきましょう。
        - 添字にcolors[5]のように範囲外の数値を指定すると、nilというオブジェクトが返ってきます。nilは何もないという意味の特殊なオブジェクトで、よく出てくるので覚えておいてください。
        
        ```ruby
        # 配列
        
        colors = ["red", "blue", "yellow"]
        
        p colors[0] # 大括弧の中の数値を添字と言う
        p colors[-1]
        p colors[0..2]
        p colors[0...2]
        p colors[5] # nil
        ```
        
        ```ruby
        % ruby hello.rb
        "red"
        "yellow"
        ["red", "blue", "yellow"]
        ["red", "blue"]
        nil
        ```
        
        - 要素の書き換えや追加は、書き換えをしたい場合にはcolors[0] = “pink” と書けばOKです。
        - 範囲を指定したい場合には、colors[1..2] = [”white”, “black”]で、一気に書き換えることもできるので覚えておきましょう。
        - 要素の末尾に何らかの要素をくっつけたい場合には、pushメソッドが使えます。
        - pushはよく使うので、colors << “silver” という書き方もできるので、覚えておきましょう。
        
        ```ruby
        colors = ["red", "blue", "yellow"]
        
        colors[0] = "pink"
        colors[1..2] = ["white", "black"]
        colors.push("gold")
        colors << "silver"
        p colors
        ```
        
        ```ruby
        % ruby hello.rb
        ["pink", "white", "black", "gold", "silver"]
        ```
        
        - 他によく使うメソッドとしては、要素の数を示すsize、要素の並び替えをしてくれるsortといったものもあるので、そちらも覚えておきましょう。
        
        ```ruby
        colors = ["red", "blue", "yellow"]
        
        p colors.size
        p colors.sort # アルファベット順にソートされる
        ```
        
        ```ruby
        % ruby hello.rb
        3
        ["blue", "red", "yellow"]
        ```

- 要点まとめ
    - 配列の表現方法
    - 要素へのアクセス方法
    - push
    - size
    - sort</details>

**<details><summary>#09 ハッシュオブジェクトを使おう</summary>**
- ハッシュというオブジェクトについて見ていきましょう。
    - ハッシュはキーと値をペアにしてまとめておくことができるオブジェクトです。
    - 例えばゲームスコアを考えてみましょう。taguchiさんが200点で、fkojiさんが400点だった場合、名前とスコアをペアにして管理したいと思います。その場合はハッシュを使えば便利なので作り方を見ていきましょう。
        - scoresという変数で管理して、ハッシュは{ }波括弧で囲います。
        - キーと値を書くのですが、それぞれを結びつけるには => を使います。
        - あとはカンマ区切りで書けばいいので、scores = {”taguchi” => 200, “fkoji” => 400}といった形になります。
        - “taguchi”、”fkoji”などのキーは、シンボルオブジェクトがよく使われます。
        - シンボルは:から始まる識別子のようなオブジェクトで、文字列を使うより動作が高速でRubyではよく使われるので覚えておいてください。
        - ハッシュをシンボルに書き換えると、{:taguchi => 200, :fkoji => 400}になります。
        - シンボルを使ったハッシュはよく使われるので、短い記法が用意されています。{taguchi: 200, fkoji: 400}
        - いろいろな書き方があるのですが、どれも使えるようにしておいてください。
        
        ```ruby
        # ハッシュ
        # - key / value
        
        # taguchi 200
        # fkoji 400
        
        scores = {"taguchi" => 200, "fkoji" => 400}
        scores = {:taguchi => 200, :fkoji => 400}
        scores = {taguchi: 200, fkoji: 400}
        ```
        
        - ハッシュのそれぞれの要素へのアクセスは、配列と同じように[ ]大括弧ですることができます。
        - 例えば、scoresにキーである:taguchiを与えると、その値である200を引っ張ってくることができます。
        - 値の書き換えもできます。fkojiさんのスコアが本当は600点だった場合はscores[:fkoji] = 600と書き換えればOKです。
        
        ```ruby
        # ハッシュ
        # - key / value
        
        # taguchi 200
        # fkoji 400
        
        # scores = {"taguchi" => 200, "fkoji" => 400}
        # scores = {:taguchi => 200, :fkoji => 400}
        scores = {taguchi: 200, fkoji: 400}
        
        p scores[:taguchi]
        scores[:fkoji] = 600
        p scores
        ```
        
        ```ruby
        % ruby hello.rb
        200
        {:taguchi=>200, :fkoji=>600}
        ```
        
    - さらに便利なメソッドもたくさんあるのでいくつか見ていきましょう。
        - 要素の数を引っ張ってくるにはscores.sizeメソッドを使ってください。
        - キーの一覧を引っ張ってきたい場合はscores.keys、値の一覧だけ引っ張ってきたい場合はscores.valuesが使えます。もしくはそのキーがあるかどうかはscores.has_key?で調べることができるのでこういったメソッドも使えるようにしておきましょう。
        
        ```ruby
        scores = {taguchi: 200, fkoji: 400}
        
        p scores.size
        p scores.keys
        p scores.values
        p scores.has_key?(:taguchi)
        ```

- 要点まとめ
    - ハッシュの表現方法
    - 要素へのアクセス方法
    - size
    - keys
    - values
    - has_key?</details>

**<details><summary>#10 オブジェクトを変換してみよう</summary>**
- いろいろな種類のオブジェクトを相互に変換したい場合を見てみましょう。
    - 例えば、xが50で、yが”3”という文字列だったとします。この時、xとyを足そうとして「p x + y」としてもうまくいかないはずです。
    
    ```ruby
    # 変換
    
    x = 50
    y = "3"
    
    p x + y
    ```
    
    ```ruby
    % ruby hello.rb
    hello.rb:6:in `+': String can't be coerced into Integer (TypeError)
    	from hello.rb:6:in `<main>'
    
    # x が数値で y が文字列だからそうなっているという意味です
    ```
    
    - x が数値で y が文字列だからです。
    - x と y を足して 53 にしたかった場合、y を数値にしてあげる必要があります。
        - もし整数に変換したい場合は、to integer という意味で「y.to_i」としてください。
        - もし浮動小数点数にしたい場合は、to float という意味で「y.to_f」としてあげてください。
    - x + y の足し算で 53 にするのではなくて、 x を文字列にしてあげて「503」にしたい場合は、逆に x の方を string にしたいので「x.to_s」としてあげればOKです。
    
    ```ruby
    # 変換
    
    x = 50
    y = "3"
    
    p x + y.to_i # to integer 整数に 
    p x + y.to_f # to float 浮動小数点数に
    p x.to_s + y # to string 文字列に
    ```
    
    ```ruby
    % ruby hello.rb
    53
    53.0
    "503"
    ```
    
    - このように違う種類のオブジェクトに変換することはよく行うので、覚えておいてください。
- ハッシュと配列の相互変換について見ておきましょう。例えば、scoresをシンボルを使ってscores = {taguchi: 200, fkoji:400} のようにハッシュで表現してみましょう。
    - これを配列に表現するには to Array(配列に) という意味で「scores.to_a」としてあげてください。こうしてあげると、キーと値が配列になった配列になります。
    
    ```ruby
    scores = {taguchi: 200, fkoji: 400}
    
    p scores.to_a
    ```
    
    ```ruby
    % ruby hello.rb
    [[:taguchi, 200], [:fkoji, 400]]
    ```
    
    - この配列をハッシュに戻すには、 to Hash という意味で「scores.to_a.to_h」とするので覚えておきましょう。
    
    ```ruby
    scores = {taguchi: 200, fkoji: 400}
    
    p scores.to_a.to_h
    ```
    
    ```ruby
    % ruby hello.rb
    {:taguchi=>200, :fkoji=>400}
    ```
    
    - こうした変換はよく行うので慣れておくようにしましょう。
- 要点まとめ
    - to_i # 整数化
    - to_f # 浮動小数点数化
    - to_a # 配列化
    - to_h # ハッシュ化</details>

**<details><summary>#11 %記法を使ってみよう</summary>**
- %を使った便利な記法についていくつか見ていきましょう。
    - 文字列を “hello” のように “” で囲ったり、式展開などが必要ない場合は ‘’ で囲ってきました。実は別の記法も用意されていて “” で囲った文字列は %Q()を使い、 %Q(hello) と書くことができます。もしくはQを省略して %(hello) でも “hello” と同じ意味になので覚えておいてください。
    - ‘’ で囲った ‘hello’ は小文字の q で %q(hello) と書くことができるので覚えておきましょう。
    
    ```ruby
    # %
    
    puts "hello"
    puts 'hello'
    
    puts %Q(hello) # puts "hello" と同じ
    puts %(hello) # puts "hello" と同じ
    puts %q(hello) # puts 'hello' と同じ
    ```
    
    - これだけだと何が便利なのかわかりづらいですが、実は文字列の中で区切り文字を使いたい場合は % を使った記法の方が見やすかったりします。
        - 例えば “” ダブルクォーテーションの中で “ ダブルクォーテーションを使いたかったり、’’ シングルクォーテーションの中で ‘ シングルクォーテーションを使いたい場合、「これらは区切り文字ではないよ」という意味で \ をつけてあげる必要があったりします。
        - 一方、 % の記法の場合はそうする必要はなく、 “ や ‘ をそのまま書けるので覚えておいてください。
        
        ```ruby
        # %
        
        puts "he\"llo" # \ が必要
        puts 'he\'llo' # \ が必要
        
        puts %Q(he"llo) # そのまま " が書ける
        puts %(he"llo) # そのまま " が書ける
        puts %q(he'llo) # そのまま ' が書ける
        ```
        
        ```ruby
        % ruby hello.rb
        he"llo
        he'llo
        he"llo
        he"llo
        he'llo
        ```
        
        - どちらも使えるようにしておくとよいかと思います。
- それからもう一つの記法ですが、配列で文字列を管理したい場合、今まで "" ダブルクォーテーションだった場合は ["red", "blue"] のように書いてきましたし、'' シングルクォーテーションの場合は ['red', 'blue'] と書いてきたかと思います。
    - こちらにも便利な記法が用意されていて "" ダブルクォーテーションで囲った文字列からなる配列は %W(red blue) と書いていけば全くこちらと同じ意味になります。
    - そして '' シングルクォーテーションで囲った ['red', 'blue'] の配列の場合は、小文字の w で %w(red blue) と書けばいいので、" や ' をたくさん書くのが面倒な場合はこういう書き方もできると覚えておいてください。
    
    ```ruby
    p ["red", "blue"]
    p ['red', 'blue']
    
    p %W(red blue) # "" ダブルクォーテーションの時は大文字のW
    p %w(red blue) # '' シングルクォーテーションの時は小文字のw
    ```
    
    ```ruby
    % ruby hello.rb
    ["red", "blue"]
    ["red", "blue"]
    ["red", "blue"]
    ["red", "blue"]
    ```

- 要点まとめ
    - %Q 、%q
    - %W 、%w</details>

**<details><summary>#12 書式付きで値を埋め込もう</summary>**
- 書式付きで文字列に値を埋め込む方法
    - 「”文字列” % 値」と書く。
    - 文字列には値の種類に応じて特殊な記号で埋め込んでいくのですが
        - 文字列だったら、 %s
        - 整数だったら、 %d
        - 浮動小数点数だったら、 %f を使います。
        - 他にもあるのですが、3つを基本として押さえておきましょう。
    
    ```ruby
    # "文字列" % 値
    # %s
    # %d
    # %f
    
    p "name: %s" % "taguchi"
    ```
    
    ```ruby
    % ruby hello.rb
    "name: taguchi"
    ```
    
    - %s に書式を指定することもできて、たとえば %10s とすると 10 桁分の幅を確保してこちらを表示してくれます。
    - なお 10 桁分を確保しつつ左寄せにしたい場合はこちらに - を付けて %-10s としてあげればいいので、これらの違いを実行して確かめてみましょう。
    
    ```ruby
    p "name: %s" % "taguchi"
    p "name: %10s" % "taguchi" # 10桁分の幅を確保して表示
    p "name: %-10s" % "taguchi" # 10桁分を確保しつつ、左寄せで表示
    ```
    
    ```ruby
    % ruby hello.rb
    "name: taguchi"
    "name:    taguchi"
    "name: taguchi   "
    ```
    
    - こうした書式も使えるようにしておきましょう。
- 数値について
    - 例えば id と rate を表示したい、そして id の場合は整数で rate の場合は浮動小数定数だった場合は "id: %d, rate: %f" としてあげましょう。
    
    ```ruby
    p "id: %d, rate: %f" % [355, 3.284]
    ```
    
    ```ruby
    % ruby hello.rb
    "id: 355, rate: 3.284000"
    ```
    
    - 書式なのですが、例えば id の方は 5 桁にしたいけれど 5 桁に満たなくて、 0 で埋めて欲しいという場合は %05d と書いてあげてください。
    - %f の方なのですが、全体の文字数が 10 文字、そのうち小数点以下が 2 文字という場合には %10.2f と指定してあげれば OK です。
    
    ```ruby
    p "id: %05d, rate: %10.2f" % [355, 3.284]
    ```
    
    ```ruby
    % ruby hello.rb
    "id: 00355, rate:       3.28"
    ```
    
    - ちなみに、こういった書式は printf や sprintf で使えることも覚えておくとよいでしょう。
        - printf は書式付きで文字列を表示するための命令です。
        - 「"文字列" % 値」の % は , にすればいいので printf("name: %10s", "taguchi") とします。
        
        ```ruby
        # printf
        # sprintf
        
        printf("name: %10s\n" , "taguchi")
        printf("id: %05d, rate: %10.2f\n", 355, 3.284)
        
        # わかりやすくするために \n で改行を付ける
        ```
        
        ```ruby
        % ruby hello.rb
        name:    taguchi
        id: 00355, rate:       3.28
        
        # \nの改行なしの場合
        % ruby hello.rb
        name:    taguchiid: 00355, rate:       3.28
        ```
        
        - sprintf は表示するのではなく、文字列を返してくれる命令になります。
        
        ```ruby
        p sprintf("name: %10s\n" , "taguchi")
        p sprintf("id: %05d, rate: %10.2f\n", 355, 3.284)
        ```
        
        ```ruby
        % ruby hello.rb
        "name:    taguchi\n"
        "id: 00355, rate:       3.28\n"
        ```
        
    - こうした書式付きでいろいろな値を表示するというのはよく行うので、基本としてこの辺りを押さえておきましょう。
- 質問:文字列に「％」を含めるにはどうすればよいですか？
    - 先生:%自身を出力するには%%とします。
- 質問:書式付きで値を埋め込むメリットがわかりません。
    - 先生:先ずは動画のサンプルのような「桁(書式)を指定するのが簡単」であることがあげられます。
    
    ```ruby
    "id: %05d, rate: %10.2f"
    ```
    
    - このような感じで、「5桁に合うように0で埋める（%05d）」や「小数点以下を2桁にする（２番目の%)」は、埋め込みを使わなくても数値を文字列に変換して工夫すればできないことはないのですが、かなり煩雑になってしまいます。なので、この「書式指定機能」はかなり便利なのです。
    - 加えまして、見た目の見通しが良くなる、のも大きなメリットです。例えば上のような数値でなくて文字列であったとしても
    - 例えば
    
    ```ruby
    "こんにちは"+personA+"さん、私は"+personB+"です。彼は"+personC+"です。"
    ```
    
    - よりも、
    
    ```ruby
    "こんにちは%sさん、私は%sです。彼は%sです。" % [personA,personB,personC]
    ```
    
    - のほうがすっきりしてみませんか。上だと変数が多くなるとどちらが”の内側なのか判断しづらくなりバグの原因になります。
    - こんな感じで書式付きの値の埋め込みには、簡潔に数値の表現を指定できる、見通しが良くなる、メリットがありますので、ぜひ活用してくださいね。
- 要点まとめ
    - “文字列” % 値
    - %s 、%d 、%f
    - printf 、sprintf</details>

**<details><summary>#13 ifで条件分岐をしてみよう</summary>**
- score が 80 より大きかった時に何らかのメッセージを出すと書いてあげましょう。
    - その場合は if のあとに条件を続けてあげて、score > 80 が真だった場合（つまり true だった場合）に行う処理を then 以下に書いてあげれば OK です。
    - ちなみに score > 80 に合致した場合はこの処理なのですが、合致しなかった場合の処理も書くことができて、その場合は else と書いてあげて else 以下にその場合の処理を書いてあげましょう。
    - ちなみに条件を繋げていくこともできて、その場合は elsif と書いてあげて条件を書いてあげてください。
    - たとえば 80 より大きくないけれど 60 より大きかった場合に何らかのメッセージを表示したい場合は「elsif score > 60 then … 」と書いてあげれば OK でしょう。
    
    ```ruby
    # if
    
    if score > 80 then
      puts "great!"
    elsif score >60 then
      puts "good!"
    else
      puts "so so ...!"
    end
    ```
    
    - ちなみに then は省略できるので覚えておきましょう。
    
    ```ruby
    # if
    # then は省略可能
    
    if score > 80
      puts "great!"
    elsif score >60
      puts "good!"
    else
      puts "so so ...!"
    end
    ```
    
    - ユーザーから入力を受け付けてみましょう。そのためのメソッドは gets です。
    - ただ、 gets で受け取るのは文字列になるのでそれを数値に変換してあげないといけません。なので、「gets.to_i」とします。
    
    ```ruby
    # if
    
    score = gets.to_i # .to_i で整数化
    
    if score > 80 then
      puts "great!"
    elsif score >60 then
      puts "good!"
    else
      puts "so so ...!"
    end
    ```
    
    ```ruby
    % ruby hello.rb
    88
    great!
    % ruby hello.rb
    77
    good!
    % ruby hello.rb
    59
    so so ...!
    ```
    
    - 条件分岐で使った > は比較演算子と呼ばれ、他にもあります。
    - 直感的で分かりやすいかと思うのですが「〜より大きい（>）」「〜より小さい（<）」「〜以上（>=）」「〜以下（<=）」そして「〜と等しい」というのは == を使ってあげてください。
    - 「〜と等しくない」というのは != です。
    - これらの比較演算子を合わせて論理演算子を使っていくことも可能です。
    - & を 2 つ繋げて && (AND) にすることもできますし OR の場合は | が 2 つで || (OR)、そして NOT の否定の場合は ! を付ければいいので覚えておきましょう。
    - それからこういった条件分岐をよくやるのですが、すごく単純な条件分岐の場合は if を後ろに書くこともできて、たとえば「puts "great!" if score > 80」といった書き方もできたりします。
    
    ```ruby
    score = gets.to_i
    
    puts "great!" if score > 80
    ```
    
    ```ruby
    % ruby hello.rb
    90
    great!
    ```

- 要点まとめ
    - if...elsif...else...and
    - gets
    - 後置のif
- #14 caseで条件分岐をしてみよう
