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
