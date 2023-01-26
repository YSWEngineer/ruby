- 2022/05/02現在のバージョンは、ruby 3.1.0p0
- 1.必要なツールの用意
    - ターミナルの準備
    - macOSにはRubyが標準でインストールされています。ruby -v コマンドを入力してRubyのバージョンを確認します。「バージョン」とは、多くのプログラミング言語では「バージョン」と呼ばれる番号で状態を管理・更新しています。
- 2.Rubyを実行してみる
    - デスクトップ上で右クリックをし、「新規フォルダ」を選択して「**ruby_lesson**
    」という名前のフォルダを作成してください。
    - エディタ(VS Code)で先程作成したフォルダ「ruby_lesson」を開き、その中に「**index.rb**
    」ファイルを作成してください。
    
    ![https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1608259497498.png](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1608259497498.png)
    
    - 作成した「index.rb」にRubyのコードを記述してみましょう。今回は以下に用意したコードをコピーして貼り付けてください。
    
    ```ruby
    puts "Hello, World!"
    puts 1 + 2
    ```
    
    - ではこのコードの実行結果を確認してみましょう。Rubyのファイルを実行するにはターミナルを使用します。エディタ上で**「Terminal」**メニュークリックし、**「New Terminal」**をクリックしてください。
    
    ![https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1608259535811.png](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1608259535811.png)
    
    - 作成した「index.rb」を実行してみましょう。Rubyファイルは、ターミナルでruby ファイル名で実行できます。
- 3.Homebrewのインストール
    - /usr/bin/ruby -e "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/master/install](https://raw.githubusercontent.com/Homebrew/install/master/install))"をターミナルで実行します。途中でPCにログインする時に使用しているパスワードの入力も求められます。この画面ではキーボードを押しても何も表示されませんが、正常に入力されていますので落ち着いてパスワードを入力し、Enterキーを押してください。時間がかかりますが、以下のような画面が表示されればインストール終了です。
    
    ![https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1524637595997.png](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1524637595997.png)
    
    - brew -v を入力して実行します。Homebrew 1.6.2のような文字が表示されれば、Homebrewは正常にインストールできています。
- 4.rbenvのインストール
    - brew install rbenv ruby-build をターミナルで実行して、rbenvをインストールしましょう。以下のような画像が表示されればインストール完了です。
    
    ![https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1524637814773.png](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/5/1524637814773.png)
    
    - rbenvを使用してRubyをインストールするのですが、その前に実行環境を確認しインストールしたrbenvの設定をしておきましょう。echo $SHELL を実行します。
    - **実行結果が /bin/bash の場合**、以下のコマンドを実行してください。
    
    ```ruby
    echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
    
    source ~/.bash_profile
    ```
    
    - 実行結果が /bin/zsh の場合、以下のコマンドを実行してください。
    
    ```ruby
    echo 'eval "$(rbenv init -)"' >>  ~/.zshrc
    
    source ~/.zshrc
    ```
    
    これでrbenvの設定は完了です。
    
- 5.Rubyのインストール
    - `rbenv install --list` をターミナルで実行します。インストールすることが可能なRubyのバージョン一覧が表示されます。この一覧の中に、`2.6.x` などの表示があるかと思います（`x`には数字が入ります）。今回は、 `2.6.5`のバージョンのRubyをインストールし、使用できるようにしていきましょう。もし`2.6.5`が一覧に無い場合は、たとえば`2.6.6`など、最後の数字が`5`以上のものをインストールしていきます。説明の都合上、以下では`2.6.5`を例に進めますので、その場合は適宜読み替えてください。
    - rbenv install 2.6.5 を実行してインストールします。インストールが終わったら、`rbenv versions` を実行します。
    - インストールしたバージョンのRubyを使用するように設定を変更しましょう。`rbenv global 2.6.5` を実行してください。これでRubyが使えるようになりました。`ruby -v` を実行して確認します。正しく設定できていれば、`2.6.5`
     と表示されたはずです。
