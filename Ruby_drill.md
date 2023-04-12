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

# 7.特定条件のみに呼応するプログラムの作成
## 問題
今日の曜日を表示するコードをDateクラスを使用して記述してください。<br>
ただし、金曜日だった場合だけ以下のように表示の内容を変えてください。<br>

（出力内容）<br>
「今日は月曜日」<br>
「今日は金曜日だ ！！！」

### ヒント
【Dateクラス】<br>
DateクラスとはRubyの標準ライブラリの機能です。Dateクラスを使うには以下の一文を記述します。
```Ruby
require "date"
```
次に、Dateクラスを用いて「今日の曜日」を取得する場合は以下のように記述します。
```Ruby
Date.today.wday
```
wdayは曜日を0(日曜日)から6(土曜日)の整数で取得することができるDateクラスに用意されているメソッドです。<br>
たとえば、以下のように使うことができます。
```Ruby
require "date"

day = Date.today.wday

puts day
```
これを実行すると、曜日に合わせた数字が出力されます。たとえば、木曜日だとすれば4が出力されることになります。
## 解答
```Ruby
require "date"

day = Date.today.wday
days = ["日曜日", "月曜日", "火曜日", "水曜日", "木曜日", "金曜日", "土曜日"]

if day == 5
  puts "今日は#{days[day]}だ！！！"
else
  puts "今日は#{days[day]}"
end
```
## 解説
日付を扱うため、RubyのライブラリにあるDateクラスを使用する。<br>
（1行目）Dateクラスをライブラリから呼び出す。<br>
（3行目）wdayメソッドを用いて曜日を0（日曜日）から6（土曜日）の整数にしたときの「今日」の値を取得する。<br>
（4行目）配列daysを定義し、日曜日（0番）〜土曜日（6番目）まで文字列を格納する。<br>
（6〜10行目）dayの値が5（金曜日）か否かで条件分岐させます。たとえば、今日が金曜日だった場合はday=5となり、daysの5番目の値である金曜日が出力される。

# 8.if→unlessへの書き換え
## 問題
次のif文を`unless`というメソッドを用いて書き換えてください。

```Ruby
if a + b > 0
  puts "計算結果は0より大きいです"
end
```

### ヒント
【unless】<br>
unlessとはifとは逆で、条件式がfalseの場合に処理が実行されます。

ifを使用した場合
```Ruby
if 条件式
  条件式がtrueの時に実行する処理
else
  条件式がfalseの時に実行する処理
end
```

unlessを使用した場合
```Ruby
unless 条件式
  条件式がfalseの時に実行する処理
else
  条件式がtrueの時に実行する処理
end
```

## 解答
```Ruby
unless a + b <= 0
  puts "計算結果は0より大きいです"
end
```

## 解説
`a + b > 0`という式は、**「a + b が0より大きいとき」にtrue**となり、その結果`end`までの処理が実行され文字列が表示される。

```Ruby
if a + b > 0
  puts "計算結果は0より大きいです"
end
```

では、上記コードのifをunlessに変更し、演算子「>」を「<」に変更した場合はどうなるか。

```Ruby
unless a + b < 0
  puts "計算結果は0より大きいです"
end
```

この場合、**「a + b が0より小さい」という条件式がfalse**の時に文字列が表示される。つまり、「a + b が0より小さくないとき」に文字列が表示される。<br>
しかしこれでは、`a + b が0`の場合でも、`「a + b が0より小さい」という条件式がfalse`となるため文字列が表示されてしまう。<br>
そのため、`a + b が0`の際に文字列を表示させないようにするために、下記のように、演算子`<=`を使用したコードにする。

```Ruby
unless a + b <= 0
  puts "計算結果は0より大きいです"
end
```
# 9.繰り返し処理
## 問題
次の要件を満たすプログラムを実装しましょう。

- 1~10の数値を順番に足し合わせる
- 足し算の合計値がターミナルに出力される

しかし、以下のような順番に並べて、足し算しただけのプログラムはNGです。

```Ruby
sum = 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10
```

ループ処理を用いて実装しましょう。

### ヒント
times文を用いることで、ループ処理を実装できます。<br>
ループ処理とは、特定の条件下にて、任意の処理を繰り返すことでした。<br>
今回の問題にループ処理を当てはめると、

- 0に1を足し、
- その結果に2を足し、
- その結果に3を足し、
- その結果に4を足し、
- その結果に5を足し、

...と10まで繰り返していきます。

これらの内容を図にすると以下のようになります。

<img width="536" alt="f4b87dd58442cf669ca8d1aff9742ccb" src="https://user-images.githubusercontent.com/115250897/231026465-9b2fe93c-337a-48e1-a6df-637f48ea459c.png">

## 解答
```Ruby
sum = 0

10.times do |i|
  sum = sum + i + 1
end

puts sum
```

もしくは自己代入演算子`+=`を使って

```Ruby
sum = 0

10.times do |i|
  sum += i + 1
end

puts sum
```

## 解説
このプログラムの考え方は以下のとおり。

1. 合計値を保存しておく変数`sum`を用意する
2. 変数`sum`に1〜10の数値を順番に足していく
3. 順番に足していく処理をtimes文の繰り返しで置き換える
4. 変数`sum`の値をターミナルに出力

1に2を足し、その結果に3を足し…と繰り返していくため、計算結果を保存しておく変数が必要になる。これを変数名`sum`として定義し、`sum`には0を代入しておく。

times文を使えば、何度も繰り返される同じ処理をまとめることができる。<br>
times文は`繰り返したい回数.times`と記載して繰り返す数を決める。今回は1〜10まで順番に足していくため、10回同じような処理が繰り返される。よって繰り返したい回数は10回。

```Ruby
sum = 0

10.times do |i|
  # 順番に足していく処理を書く
end
```

times文では、変数`i`の中に繰り返しの回数が数値として自動で代入される。よって、変数`i`を使えば繰り返しの回数を変数`sum`に足していくことができる。
ただし、プログラムなので1回目のiの数値は0となる。よって`sum`に足すのは1増やした`i + 1`にする必要がある。

```Ruby
sum = 0

10.times do |i|
  sum += i + 1
end
```

最後に`puts`メソッドで`sum`をターミナルに出力して終了。

```Ruby
sum = 0

10.times do |i|
  sum += i + 1
end

puts sum
```

# 10.配列を利用したrubyプログラムの作成
## 問題
以下の配列から任意の数字を探して何番目に含まれているかという結果を返すsearchメソッドを、`each_with_index`を用いて作成しましょう。

```Ruby
input = [3, 5, 9 ,12, 15, 21, 29, 35, 42, 51, 62, 78, 81, 87, 92, 93]
```

### 雛形
```Ruby
def search(target_num, input)
  # 処理を記述
end

input = [3, 5, 9 ,12, 15, 21, 29, 35, 42, 51, 62, 78, 81, 87, 92, 93]
# 呼び出し例
search(11, input)
```

### 出力例
search(5, input) → 2番目にあります

search(12, input) → 4番目にあります

search(7, input) → その数は含まれていません

### ヒント
`each_with_index`は、Rubyに標準で組み込まれているメソッドの1つです。要素の繰り返し処理と同時に、その要素が何番目に処理されたのかも表すことができます。

以下のように記述します。

```Ruby
配列名.each_with_index  do |item, i|

end
```

具体的には以下のように使うことができます。

```Ruby
fruits = ["メロン", "バナナ", "アップル"]

fruits.each_with_index do |item, i|
 puts "#{i}番目のフルーツは、#{item}です。"
end
```

これを実行すると、以下のような出力結果が得られます。

```Ruby
0番目のフルーツは、メロンです。
1番目のフルーツは、バナナです。
2番目のフルーツは、アップルです。
```

## 解答
```Ruby
def search(target_num, input)

  input.each_with_index do |num, index|
    if num == target_num
      puts "#{index + 1}番目にあります"
      return
    end
  end
  puts "その数は含まれていません"
end

input = [3, 5, 9 ,12, 15, 21, 29, 35, 42, 51, 62, 78, 81, 87, 92, 93]
search(11, input)
```

## 解説
### searchメソッドを呼び出す際の処理
まず、配列`input`を定義する。

次に、`searchメソッド`を呼び出す際に、11とinputという変数を実引数としてセットする。<br>
呼び出されたsearchメソッドでは、実引数でセットした値を仮引数target_numとinputとして受け取る。

### searchメソッド内の処理
まず、input.each_with_indexでは、inputに格納されている要素を1つ1つ`num`として取り出すと同時に、要素毎に割り当てられている添字を`index`として取得する。

次に、if文で`num == target_num`という条件式を設定する。<br>
ここでは、inputから取り出された要素numと、target_numが等しいかを判別している。

numとtarget_numが等しければ、numがinputの中の何番目に含まれているかが出力される。<br>
`#{index + 1}`としているのは、配列が0番目から始まることを考慮するため。

numとtarget_numが等くなければ、「その数は含まれていません」と出力される。

今回は、引数で渡した「11」は配列inputには含まれておらず、条件には当てはまらないため、「その数は含まれていません」と出力される。

# 11.特定の文字列を検知するプログラムの実装
## 問題
以下の要件を満たすcheck_nameメソッドを実装しましょう。

- 名前を入力すると「登録が完了しました」という文字列を出力すること
- 名前の中にピリオド(.)がある場合は、「 "!エラー!記号は登録できません"」という文字列を出力すること
- 名前の中に空白（半角のみ）がある場合は、「 "!エラー!空白は登録できません"」という文字列を出力すること

### 雛形
```Ruby
def check_name(str) 
  # 処理を記述
end

puts "登録したい名前を入力してください(例)YamadaTaro"
str = gets
check_name(str)
```

### 出力例
YamadaTaro → 登録が完了しました

Yamada.Taro→!エラー!記号は登録できません

Yamada Taro → !エラー!空白は登録できません

### ヒント
include?メソッドを使用しましょう。

include?メソッドは、指定した値が配列や文字列内に含まれているかを判定するメソッドです。指定した値が含まれている場合はtrueを、含まれていない場合はfalseを返り値として返します。

```Ruby
array = ["foo", "bar"]
puts array.include?("bar")
# => true
puts array.include?("hoge")
# => false
```

## 解答
```Ruby
def check_name(str) 
  if str.include?(".")
    puts "!エラー!記号は登録できません"
  elsif str.include?(" ")
    puts "!エラー!空白は登録できません"
  else
    puts "登録が完了しました"
  end
end
puts "登録したい名前を入力してください(例)YamadaTaro"
str = gets
check_name(str)
```

## 解説
1行目から9行目で`check_name`メソッドを定義し、その定義した`check_name`メソッドを13行目で呼び出している。その際、引数にはgetsメソッドで入力された文字列を渡している。

`check_name`メソッドでは、「ピリオドや空白（半角スペース）がない場合は登録を行い、ピリオドや空白がある場合はエラーを出す」という条件分岐を行うためにif文を使用している。

2行目から8行目にわたるif文による条件分岐では、1行目の仮引数`str`で受け取った文字列に対してinclude?メソッドを使用し、`”.”`(ピリオド)と`” ”`(半角スペース)がないかを判断している。

注意点として、if文は条件が当てはまった時点で処理が終了するため、「ピリオドや空白があるかどうか」という条件式を先に記述する必要がある。

そして、出力例を参考にそれぞれの場合で出力させる値を、putsメソッドを用いて記述して、このコードは完成する。
