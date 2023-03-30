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
