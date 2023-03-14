# 条件分岐
## if文
```
if ( 条件式 ) {
  条件式を満たす時に実行する処理
}
```
Rubyのif文との主な違いは以下の3点
1. 条件式を()で囲む
2. 処理を{}で囲む
3. elsifではなくelse if

# 繰り返し処理
## 拡張for文
```
for ( 要素を格納する変数宣言  :  配列あるいはArrayListの変数名) {
  取り出した要素を使用して行う処理
}
```
1. 配列、あるいはArrayListから要素を1つ取り出す
2. 取り出した要素を変数に代入する
3. {}内の処理を行う
4. 配列、あるいはArrayListの要素数分だけ処理を繰り返す

たとえば…
```
for(int score : scores) {
  System.out.println(score);  
}
```
1. 配列、あるいはArrayList「scores」から要素を1つ取り出す
2. 取り出した要素を、定義した変数「score」に代入する
3. {}内の処理（=scoreを表示する）を行う
4. 「scores」の要素数分だけ処理を繰り返す

# メソッド
Rubyのメソッドとの主な違いは以下の4点
1. ファイルを実行すると自動的にmainメソッドが実行される（mainメソッドは必ず以下のように決められた通りに記述をする）
2. 返り値のデータ型を指定する必要がある
3. 引数がないメソッドでも定義時に()の省略はできない
4. 「def」「end」の代わりに、{}でコードを囲む
```
class Main {
  public static void main(String[] args) {  
    実行したい処理
  {
}
```

## 引数を使用しないメソッド
```
class Main {
  public static void main(String[] args) {  
    sayHello();
  }

  public static void sayHello() {
    System.out.println("Hello World");
    return;
  }
}
```
1. Mainクラスのmainメソッドが実行される
2. sayHelloメソッドが実行され、「Hello World」が表示される
