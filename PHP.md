# PHPの特徴
- Webアプリケーションの開発に適している
- HTMLに埋め込むことができる
- 動的にWebページを作成する機能を数多く備える
- ブログサービスなどを設置できるWordPressはPHPで作られている

# メッセージの表示
コードの記述方法は以下のとおり`<>`と`?`で全体を囲み、phpのコードである旨の宣言が必要。<br>
また、コードの行末に「;（セミコロン）」が必要。

```php
<?php
    #ここにコードを記述する;
?>
```

データを表示させる命令である`echoメソッド`を使用してメッセージを表示する。Rubyにおけるputsメソッドと同じ働き。

```php
<?php
    echo "Hello World";
?>
```

複数行のコードは上から順番に実行する。<br>
ただし、`echo`だけでは改行しないため、改行するには`\n`を付け加える。「\（バックスラッシュ）」の入力方法は`option + ¥`。

```php
<?php
    echo "Hello paiza\n";
    echo "Hello paiza";
?>
```

# コメントを書く
コードの頭に`#`を付けることで、その行はコメントになり、プログラムの実行に影響しなくなる。

```php
<?php
    # コメントを書く
    echo "Hello World";
?>
```
`#`の代わりに`//`を使用することもできる。

```php
<?php
    // コメントを書く
    echo "Hello World";
?>
```
また、`/* */`で囲むことでもコメントとして扱うことができる。複数行にまたがる記述の場合はこちらが便利。

```php
<?php
    /* コメントを書く
    コメントを書く */
    echo "Hello World";
?>
```

# 変数
PHPの変数は、頭に`$`を付ける。

```php
<?php
    $greeting = "Hello world";
    echo $greeting;
?>

# Hello world
```

また、変数名の命名については以下のような決まりがある。
- 1文字目：アルファベット、アンダーバー
- 2文字目以降：アルファベット、アンダーバー、数字
- 慣習として日本語(全角)で書かない
- 慣習として小文字にする

# 文字列の連結
文字列同士を連結させたい場合は、`.`でつなぐ。

```php
<?php
    $name = "kkoemna";
    echo $name . "さん、冒険にようこそ";
?>

# kkoemnaさん、冒険にようこそ
```

# データを受け取る
以下のコードにより、プログラムの実行時にデータを受け取る。

```php
trim(fgets(STDIN))
```

- trim関数：データの前後にある空白や改行を削除して整える
- fgets関数：指定した場所から1行のデータを受け取る
- STDIN：標準入力を表す

```php
<?php
    $name = trim(fgets(STDIN));
    echo "Hello " . $name;
?>
```

上記コードでは、受け取ったデータを`$name`という変数に代入して、echoメソッドにより文字列「Hello」と連結して表示する。

また、文字列に限らず数値も同様のコードで受け取ることができる。

```php
<?php
    $number = trim(fgets(STDIN));
    echo $number * 10;
?>
```

# 条件分岐
## if文の基本
```php
<?php
    $name = trim(fgets(STDIN));

    if ($name == "PHP") {
        echo "Welcome\n";
    }
?>
```

上記は、`if文`を用いて、受け取ったデータが`PHP`と一致したら、`Welcome`と表示するプログラム。

Rubyと違い、`条件式を()内`に記述し、`条件式に一致する場合の処理を{}内`に記述する。

```php
<?php
    if (条件式) {
        条件式に一致する場合の処理;
    }
?>
```

## 比較演算子
比較演算子はRubyと同じ。

- `a == b` aはbと等しい
- `a != b` aはbと等しくない
- `a > b` aはbより大きい
- `a < b` aはbより小さい
- `a >= b` aはb以上
- `a <= b` aはb以下

## elseとelseif
### else
```php
<?php
    $name = trim(fgets(STDIN));
    echo "Hello " . $name . "\n";

    if ($name == "PHP") {
        echo "Welcome\n";
    } else {
        echo "Goodbye\n";
    }
?>
```

上記では、条件と一致しなかった場合、`Goodbye`と表示する。

条件と一致した場合の処理を{}で閉じたあと、`else`でつないで、条件と一致しなかった場合の処理を{}内に記述する。

### elseif
```php
<?php
    $name = trim(fgets(STDIN));
    echo "Hello ".$name."\n";

    if ($name == "PHP") {
        echo "Welcome\n";
    } elseif ($name == "php") {
        echo "Good morning\n";
    } else {
        echo "Goodbye\n";
    }
?>
```
上記では、変数`$name`が`php（小文字）`の場合、`Good morning`と表示する。

前条件の処理を{}で閉じたあと、`elseif`でつないで、新たな条件式を()内に記述し、それに一致する場合の処理を{}内に記述する。

# 繰り返し処理
## for文の基本
```php
<?php
    $greeting = "Hello world";
    for ($i = 0; $i < 5; $i++) {
        echo $greeting . "\n";
    }
?>
```

上記は、`for文`を用いて、$greeting（Hello worldが格納されている）を`5回`繰り返し表示するプログラム。

for文の構成は以下のとおり。

```php
<?php
    for (初期値; 繰り返し条件; 変化分) {
        繰り返したい処理;
    }
?>
```

先ほどの例を噛み砕いて説明すると、

```php
for ($i = 0; $i < 5; $i++)
```

「まず繰り返し処理に使う`$i`という変数を定義するよ。最初は`0`からカウントを始めて、`$i`が`5より小さい間`は処理を繰り返してね。繰り返すたび`$i`に`1ずつプラス`していってね。`$i`が`5を超えたら`繰り返し処理は終了だよ。」

という意味。
