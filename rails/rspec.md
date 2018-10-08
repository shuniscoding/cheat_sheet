# Setup procedure
1. Gemfile の `group :development, :test do` に `gem'rspec-rails', '~> 3.6.0'` を挿入する
2. 
```
$ bundle install
```
3. spec directry などの作成
```
$ bin/rails generate rspec:install
``` 
4. `.rspec` のファイルが作られるので、そこに`--format documentation` を挿入する。RSpec の出力がドキュメント形式になり、読みやすくなる。
5. `gem 'spring-commands-rspec'`を`Gemfile の :development グループ`に挿入する。Springというpreloaderを利用できるので、テストスイートの起動時間が早くなる。
6.
```
$ bundle install
```
7. 新しいbinstubの作成。bin ディレクトリ内に rspec という名前の実行用ファイルが作成される。
```
$ bundle exec spring binstub rspec
```
8. 以下を実行し出力結果が表示されたらOK
```
$ bin/rspec
```
9. rails generate コマンドを使ってアプリケーションにコードを追加 する際に、RSpec 用のスペックファイルも一緒に作ってもらうよう Rails を設定
  * onfig/application.rb に以下を追加(不要なSpecは`false`にしておく)
    ```ruby
    config.generators do |g|
      g.test_framework :rspec,
        fixtures: false,
        view_specs: false,
        helper_specs: false,
        routing_specs: false
    end
    ```