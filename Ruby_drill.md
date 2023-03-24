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
