# 条件分岐
## if文
```java
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
```java
for ( 要素を格納する変数宣言  :  配列あるいはArrayListの変数名) {
  取り出した要素を使用して行う処理
}
```
1. 配列、あるいはArrayListから要素を1つ取り出す
2. 取り出した要素を変数に代入する
3. {}内の処理を行う
4. 配列、あるいはArrayListの要素数分だけ処理を繰り返す

たとえば…
```java
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
```java
class Main {
  public static void main(String[] args) {  
    実行したい処理
  {
}
```

## 引数がないメソッド
引数がない場合も()を省略できない
```java
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

## 引数があるメソッド
仮引数（受け取る側）は変数名「number」だけでなくデータ型「int」も指定する必要がある
```java
class Main {
  public static void main(String[] args) {
    var answer = square(5);
    System.out.println(answer);
  }

  public static int square(int number){
    return number * number;
  }
}
```
1. Mainクラスのmainメソッドが実行される
2. 変数answerに代入するsquareメソッドが実行される際に引数「5」を渡す
3. squareメソッドが引数「5」を受け取り、乗算処理をおこなう
4. 結果を変数answerに代入し、それを表示する処理をおこなう

# オブジェクト指向
## オブジェクト指向とは
オブジェクトと呼ばれるパーツを連携させて機能を実現させる仕組みのこと。<br>
現実世界でいうチームのようなもの。

例えば、複数人で大量のカレーを作りたいという場合、すべての工程を1つ1つ全員で取り組むよりも、
- 買い出しに行くチーム
- 野菜を切るチーム
- 肉を切るチーム

などにチームを分けて、必要な材料や道具などをそれぞれのチームに配って取り組む方が効率がいい。<br>
このカレー作りの「チーム」に当たるのが、オブジェクト指向における「オブジェクト」。

## オブジェクトの特徴
### ①1つのオブジェクトには1つの責務がある
- データの入れ物になるオブジェクト
- フォームからデータを受け取るオブジェクト
- SQLを発行するオブジェクト
- 上記のオブジェクトをコントロールするオブジェクト

など、1つのオブジェクトには1つの機能を持たせるよう設計する。<br>
これを「単一責任の原則」という。

### ②オブジェクトにはメソッドと変数が含まれる
オブジェクトはメソッドと変数をひとまとめにしたもの。<br>
メソッドはチームに配属されたメンバーのようなもの。<br>
メンバーが肉や野菜を加工するように、メソッドはオブジェクトないの変数の変更や参照といった処理を担う。

### ③他のオブジェクトに公開するメソッドや変数は必要最低限のもののみとする
メソッドは別のオブジェクトの変数に直接アクセスしない。<br>
あるメソッドが別のオブジェクトの変数にアクセスしたい場合、相手方のオブジェクトに含まれる「取得用のメソッド」に対して、データ取得を依頼する。<br>
カレー作りでいうと、例えば、じゃがいもの皮剥きが追加で10個必要になった場合、手が空いている他のチームのメンバーが直接手伝うのではなく、野菜チームに「じゃがいもの皮剥き10個追加お願い！」と依頼する。<br>
この、他のオブジェクトに必要以上に干渉しないようにする考え方を「カプセル化」という。

# 開発環境
Rubyで使用した「Visual Studio Code」でJavaの開発をおこなうこともできるが、Javaの専用開発環境である「IntelliJ IDEA」を使用することが多い。<br>
「IntelliJ IDEA」は、Java開発者の70%以上が使用していると言われる代表的な開発環境。<br>
[IntelliJ IDEA のダウンロード](https://www.jetbrains.com/ja-jp/idea/download/#section=mac)

# フレームワーク
Javaのウェブアプリのフレームワークとして「Spring Boot」を使用する。<br>
これは、Rubyにおける「Ruby on Rails」に該当するもの。<br>
[Spring Initializr（プロジェクト作成)](https://start.spring.io/)

# アノテーション
アノテーションは「注釈」という意味で、クラスやメソッドに特別な意味を持たせるという役割がある。<br>
クラスやメソッドの定義の直前に「@〇〇」と記述する。<br>
たとえば…
```Java
@Controller
public class PostController {

}
```
@Controllerは、そのクラスがコントローラーであることをSpringに伝えるためのアノテーション。<br>
上記の例でいうと、「PostController」クラスがコントローラーとして扱われるようになる。

```Java
@GetMapping("/hello")
public String showHello(){

}
```
@GetMappingは、ブラウザで入力されたURLと、実行されるメソッドを紐づけるためのアノテーション。<br>
上記の例でいうと、「ルートパス/hello」と入力された場合、「showHello」メソッドが実行される。

# テンプレートエンジン
Javaのフレームワーク「Spring Boot」のテンプレートエンジンとして「Thymeleaf」を使用する。<br>
これはRubyのRailsにおける「ERB」に該当するもの。<br>
コントローラーとビューのコードを分離して管理しやすくすることができる。

## Thymeleafの使い方
①表示させるためのHTMLを作成する<br>
「main」→「resources」→「templates」内にHTMLファイルを作成する。ここではファイル名は「hello.html」とする。<br>
②コントローラーから①のHTMLファイルを読み込めるようにする<br>
```Java
@Controller
public class PostController {
    @GetMapping("/hello")
    public String showHello(){
        return "hello";
    }
}
```
5行目の`return "hello";`が、表示するHTMLファイルの名称を指定している。<br>
`return "hello";`と記述することで、「templates」フォルダにある「hello.html」を呼び出すことができる（.html部分は省略可能）。<br>

## Thymeleafでの変数の扱い方
Sping Bootでは、Model型のオブジェクトを使用して、以下の流れで変数を渡す。<br>
1. コントローラーの引数でModelオブジェクトを受け取る
2. Modelオブジェクトに、ビューで表示させたいデータを追加する
3. ビューでModelオブジェクトのデータを読み込む
```Java
@GetMapping("/hello")
public String showHello(Model model){
    var sampleText = "サンプルテキスト";
    model.addAttribute("sampleText", sampleText);
    return "hello";
}
```
- 2行目は「ここで定義するshowHelloメソッドを実行するときには、Modelオブジェクトの変数modelを引数として受け取るよ」という意味。
- 3行目は「文字列サンプルテキストを変数sampleTextとして定義するよ」という意味。
- 4行目は「変数modelに変数sampleTextの内容を追加するよ」という意味。

# エンティティ
エンティティとは、データベースと連携する際に、データを格納するためのオブジェクト。<br>
エンティティには、テーブルの各カラムに対応した変数を用意する。<br>
「id」と「memo」というカラムがある場合、エンティティの変数として「id」と「memo」を作成する。<br>
Javaのプログラムからデータベースにデータを保存する際も、逆にデータを読み込む際もこのエンティティを使用する。
```Java
package in.techcamp.firstapp;

import lombok.AllArgsConstructor;
import lombok.Data;

@AllArgsConstructor
@Data
public class PostEntity {
    private long id;
    private String memo;
}
```
Lombokというライブラリを使用して上記ようにリファクタリングをするのが一般的。<br>
アノテーション「@AllArgsConstructor」はコンストラクタを、「@Data」はゲッターとセッターを省略することができる。

# リポジトリ
リポジトリとは、Javaでデータベースを利用する際に必要な、SQLの操作をメソッドとして定義するもの。<br>
Railsでは、Javaのリポジトリに相当するものはあらかじめ用意されていた。<br>
例えば、RailsではTweet.allのようにallメソッドを実行することで、Tweetsテーブルのデータ全件を取得することができるが、これは、allメソッドを実行すると「select * from tweets」というSQLが発行されることがあらかじめ定義されているため。<br>
このような定義は、Javaでは自分で実装する必要がある。その際使用するのがリポジトリ。<br>
リポジトリを作成する際は`「クラス」ではなく「インターフェース」を選択する`
```Java
package in.techcamp.firstapp;

import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface PostRepository {
    @Select("select * from posts")
    List<PostEntity> findAll();
}
```
このリポジトリでは、postsテーブルから全件データを取得するための「findAll」というメソッドを定義している。<br>
MyBatisでSelect文を使ったメソッドを定義する場合は、以下のように記述する。
```Java
@Select("発行したいSQL")
返り値のデータ型 メソッド名;
```
上記の例に当てはめると以下の通り。
```Java
@Select("select * from posts")
List<PostEntity> findAll();
```

# Form
Formを作成するにあたって、以下の3つのステップに分けて学ぶ。
1. Formクラスを作成する
2. コントローラーを変更する
3. ビューを作成する

## ①Formクラスを作成する
Formクラスとはフォームに入力されたデータを格納するためのクラス。<br>
Railsの場合、フォームで入力されたデータを受け取るために、「params」というハッシュを利用した。<br>
paramsはRailsによって自動的に生成され、コントローラー内で参照することにより入力されたデータを保存することができた。<br>
このparamsに代わるものとして、Javaでは「Formクラス」を自前で作成する。
```Java
package in.techcamp.firstapp;

import lombok.Data;

@Data
public class PostForm {
    private String memo;
}
```
## ②コントローラーを変更する
①で作成したFormクラスをビューに渡すことによって、フォームの入力内容とFormクラスを関連付ける。<br>
↓変更後の「PostController」のコード
```Java
package in.techcamp.firstapp;

import lombok.RequiredArgsConstructor;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ModelAttribute;

@Controller
@RequiredArgsConstructor
public class PostController {
    private final PostRepository postRepository;

    @GetMapping("/hello")
    public String showHello(Model model){
        var sampleText = "サンプルテキスト";
        model.addAttribute("sampleText", sampleText);
        return "hello";
    }

    @GetMapping
    public String showList(Model model){
        var postList = postRepository.findAll();
        model.addAttribute("postList", postList);
        return "index";
    }

    @GetMapping("/postForm")
    public String showPostForm(@ModelAttribute("postForm") PostForm form){
        return "postForm";
    }
}
```
`@ModelAttribute`というアノテーションは、任意のデータをModel型のオブジェクトに格納することができる。<br>
Spring BootではこのModel型オブジェクトは、データの一時保管場所のように活用することができる。<br>
コントローラーでこの保管場所にデータを保管しておき、それをビューで呼び出すという使い方をする。<br>
↓具体的な使い方
```Java
@ModelAttribute("呼び出すときの名称") 保存したい変数のデータ型　保存したい変数
```
↓今回の例でいうと
```Java
@ModelAttribute("postForm") PostForm form
```
このコードによって、「PostForm型」の「変数form」を登録して、後で「postForm」という名前で呼び出すことができるよ、という意味になる。

## ③ビューを作成する
「postForm.html」というファイルを作成する
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
  <meta charset="UTF-8">
  <title>新規投稿</title>
</head>
<body>
<h1>新規投稿ページ</h1>
<form action="#" th:action="@{/posts}" th:method="post" th:object="${postForm}">
  <input type="text" id="summaryInput" th:field="*{memo}">
  <button type="submit">作成</button>
</form>
</body>
</html>
```
上記の記述のうち、以下のコードに注目。
```html
<form action="#" th:action="@{/posts}" th:method="post" th:object="${postForm}">
```
上記のコードは、Thymeleafを使って、以下の３つの指定をおこなっている。<br>
`th:action="@{/posts}"`は、フォームで投稿がおこなわれた際に次にアクセスするURLを指定するための記述。ここでは`/posts`を指定している。<br>
`th:method="post"`は、フォームで投稿がおこなわれた際に送信するHTTPメソッドを指定するための記述。ここでは投稿機能を実装しているので、HTTPメソッドは`POST`を指定する。<br>
`th:object="${postForm}"`は、フォームの投稿内容を紐付けるFormクラスを指定するための記述。この記述によって、コントローラーで設定した`postForm`とフォームを紐付けている。<br>
