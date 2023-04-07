# 1.ハッシュの基礎
## 問題
```Ruby
puts hash.keys
puts hash.values
```
上記のメソッドを実行したときに
```Ruby
one
two
three
1
2
3
```
とターミナルに表示されるような変数hashを作成するためのコードをシンボルを使って記述してください。
## 解答
```Ruby
hash = { one: 1, two: 2, three: 3 }
```

# 2.二重ハッシュ
## 問題
配列の内部に、複数のユーザーの情報をハッシュとして持つ変数user_dataがあります。
```Ruby
user_data = [
 {user: {profile: {name: 'George'}}},
 {user: {profile: {name: 'Alice'}}},
 {user: {profile: {name: 'Taro'}}},
]
```
user_dataを利用して、全てのユーザーの名前だけが出力されるようにRubyでコーディングしてください。
ただし、出力結果は次のようになるものとします。
```Ruby
George
Alice
Taro
```
## 解答
```Ruby
user_data.each do |u|
  puts u[:user][:profile][:name]
end
```
あるいは
```Ruby
user_data.each{ |u| puts u.dig(:user, :profile, :name) }
```
## 解説
ハッシュから特定の値を取得する場合は、その値に対応するキーを指定する。<br>
`ハッシュ[取得したい値のキー]`

二重ハッシュから特定の値を取得する場合は、取得したい値のキーまで連続して指定する。<br>
`ハッシュ[取得したい値のキー][取得したい値のキー]`

今回取得したい値は、「George」「Alice」「Taro」という値。<br>
取得したい値に対応するキーは「nameと」いうキー。<br>
そのため、「name」というキーまで連続して指定すると、「George」「Alice」「Taro」という値を取得できる。<br>
`ハッシュ[:user][:profile][:name]`

また、今回は配列の中にハッシュが格納されているため、each文でハッシュの1つ1つを取り出した上で、上記の記述を行うことが必要。
```Ruby
user_data.each do |u|
  puts u[:user][:profile][:name]
end
```
# 3.値に名前をつけて使おう
## 問題
国語が80点、英語が50点、数学が70点の場合のテストの平均点をターミナルに出力するプログラムを記述してください。<br>
条件1：このプログラムでは各教科の点数を変数を使って定義してください。<br>
条件2：出力結果は以下のようになるようにコードを書きましょう。
```Ruby
３教科の平均点は、◯点です。
```
## 解答
```Ruby
japanese_score = 80
english_score = 50
math_score = 70

average_score = (japanese_score + english_score + math_score) / 3

puts "3教科の平均点は、#{average_score}点です。"
```
## 解説
「変数を使って」と指定があるため、各教科の点数をそれぞれ変数として定義する。<br>
変数名はjapanese_score、japanese、kokugo_score、kokugoなどの分かりやすい名前をつけることが望ましい。
```Ruby
japanese_score = 80
english_score = 50
math_score = 70
```
また、平均点に関しても変数を使うほうが望ましい。<br>
変数を使わない場合は以下のようになる（よくない例）。
```Ruby
puts "3教科の平均点は、#{(japanese_score + english_score + math_score) / 3}点です。"
```
これだとコードが読みにくく、(japanese_score + english_score + math_score) / 3が何を指しているのかを、見ただけで判断することが難しい。<br>
そこで平均点も以下のように変数として定義する。
```Ruby
average_score = (japanese_score + english_score + math_score) / 3
```
平均点の出力の際には、文字列と数値の連結となるので、式展開かto_sメソッドを使うこと。
# 4.クラスとインスタンス
## 問題
```Ruby
class Article

  def initialize(author, title, content)
    @author = author
    @title = title
    @content = content
  end

end
```
上記のコードに追加を行い、以下の出力結果を得られるようにしてください。ただし、クラスとインスタンスを使用するものとします。
```Ruby
著者: 阿部
タイトル: Rubyの素晴らしさについて
本文: Awesome Ruby!
```
## 解答
```Ruby
class Article

  def initialize(author, title, content)
    @author = author
    @title = title
    @content = content
  end

  def author
    @author
  end

  def title
    @title
  end

  def content
    @content
  end

end

article = Article.new("阿部", "Rubyの素晴らしさについて", "Awesome Ruby!")
puts "著者: #{article.author}"
puts "タイトル: #{article.title}"
puts "本文: #{article.content}"
```
## 解説
Article.newでインスタンスを生成し、変数articleに代入する。その際に、`阿部`、`Rubyの素晴らしさについて`、`Awesome Ruby!`の3つを実引数に指定する。<br>
initializeメソッドを定義して、インスタンス変数を宣言する。実引数として指定した値を、仮引数の`author`、`title`、`content`にそれぞれ渡している。<br>
それにより、initializeメソッドで宣言されたインスタンス変数に、`阿部`、`Rubyの素晴らしさについて`、`Awesome Ruby!`という3つの値が代入される。<br>
上記インスタンス変数の値を返すための専用のメソッド3種をそれぞれ定義する。<br>
最後に定義づけたメソッドを呼び出す。
# 5.メソッドの使い方
## 問題
以下のプログラムを実行するとエラーが起きます。<br>
①エラーが起きた原因<br>
②正しいソースコード（引数を用いたコードにしましょう）<br>
をそれぞれ答えてください。
```Ruby
price = 300

def calculate_price_with_tax
  tax = 0.1
  return price + price * tax
end

calculate_price_with_tax
```
## 解答
①エラーが起きた原因<br>
メソッドの外側で定義した変数は、メソッドの内側では使えない。そのため、1行目のpriceはcalculate_price_with_taxメソッドの中では使えずにエラーが起きてしまった。

②正しいソースコード
```Ruby
price = 300

def calculate_price_with_tax(price)
  tax = 0.1
  return price + price * tax
end

calculate_price_with_tax(price)
```
## 解説
メソッドの中と外は完全に別の世界であり、メソッドの中から外にある変数を使ったり、逆にメソッドの外から中にある値を使うことはできない。<br>
唯一、メソッドの中と外を繋ぐ役割が「引数」と「返り値」である。<br>
今回の問題文のコードでは、変数priceの定義はメソッドの外で行なっていたにも関わらず、メソッドの中で変数priceをそのまま使おうとしたことがエラーの原因になった。<br>
以下の通り引数と返り値を用いることで、メソッドの外側から内側に正しく値を渡すことができる。<br>
1. メソッドの呼び出しを`メソッド名(渡したい値)`と書く
2. メソッドの定義を`def メソッド名(受け取った値を入れる変数名)`と書く
# 6.引数の基礎
## 問題
"晴れ" という文字列を引数で渡した時に
```
明日の天気は晴れです
```
とターミナルに表示されるようなメソッドを作成してください。<br>
呼び出し方：get_weather_forecast("晴れ")
## 解答
```Ruby
def get_weather_forecast(weather)
  puts "明日の天気は#{weather}です"
end

get_weather_forecast("晴れ")
```
## 解説
「明日の天気は〇〇です」の「〇〇」に任意の文字列（今回は「晴れ」）を表示したいので、引数を使用する。<br>
「〇〇」にはメソッドの呼び出し元の引数に渡した文字列が表示される。<br>
引数で渡した文字列を表示させたいので、文字展開を使用している。
