# SystemSoftware
システムソフトウェアの板書

# 第１回講義資料参考
## プログラミング言語
- プログラミング言語
  - 低水準プログラミング言語
    - ハードウェアアーキテクチャを反映した言語構造
    - 特定のハードウェアで高速に動作
  - 高水準プログラミング言語
    - ハードウェアアーキテクチャを意識させない言語構造
    - 人間がプログラミングしやすい
   
## 低水準プログラミング言語
- 機械語
  - CPUが直接解読可能な2進数データ
  - 機械語プログラムをネイティブコードと呼ぶこともある
  
- アセンブリ言語
  - CPU命令レベルで機械語に対応するプログラミング言語
  - 文字列等を用いて少し読みやすく表す
  - OSのカーネルプログラムや高速数値演算等で利用
  
- 中間言語
  - 低水準・高水準言語の中間の性質をもつ
  - pascalのPコード,Javaのバイトコード(Bytecode)
  
## 高水準プログラミング言語
- 手続き型プログラミング言語
  - COBOL
  - Pascal
  - Java
  - C,C++
  - Basic
  
- 宣言型プログラミング言語
  - Lisp
  - Prolog
  - Haskell

## コンパイラ
- あるプログラミング言語Lsで書かれたプログラムを別のプログラミング言語Ltで書かれたプログラムへ自動変換するソフトウェア
  - 変換元:高水準プログラミング言語
    - 原始プログラム
    - ソースプログラム
    - 原始コード
    - ソースコード
  - 変換先:低水準プログラミング言語
    - 目的コード
    - オブジェクトコード
    - 目的プログラム
    - オブジェクトプログラム
 
## インタプリタ
- ソースプログラムを逐次実行しながら実行
- プログラムを変換するのではなく、そのまま実行
- 総合開発環境に組み込んだ場合、プログラムを作成しながら実行可能
- 実行毎に解析処理を行うため、実行速度が遅い
- Perl,Ruby,Python,PHPなど

## コンパイラインタプリタ
- 中間言語を介した実行を行う
- コンパイラがソースプログラムを中間コードに変換後、その中間コードをインタプリタが逐次実行する
- Pascal,Java

## コンパイラの処理概要
- コンパイラにおけるプログラムの変換について
  - フロントエンド
    - 字句解析
    - 構文解析
    - 意味解析
  - バックエンド
    - コード最適化
    - コード生成
  
# 第2,3回講義資料参考
## 解説木
- 生成規則から生成された文の構造を示す図
- 木構造で表現
- 文の構造を調べる仕事が構文解析
- 構文解析の結果が解説木または構文解析木

# 第4回講義資料参考
## 字句解析
- コンパイラが最初に行う仕事
- テキスト(ソースプログラム)から単語(トークン:token)を切り出す作業
- トークンはソースプログラムを構成する語彙(lexicon)、単語に相当
- トークンの定義が厳密に与えられなければ字句解析器を作ることができない
- トークンの文脈自由文法よりも正規表現で定義可能
- 字句解析器の開発は，正規表現と有限オートマトンの理論を用いると半自動化できる

## グラフ
- グラフ（graph）とは，頂点の集合と，頂点と頂点を結ぶ線分の集合のこと．
- 頂点をノード(node）または節，頂点を結ぶ線を辺（edge）と呼ぶ．
- 計算機科学の世界で使用されるグラフの例として，木（tree）がある．
- 辺に向きをもたせたものを有向グラフと呼ぶ．方向がある辺を有向辺（directed edge），有向辺の両端にあるノードのうち，遷移元のノードを先行節（predecessor），遷移先のノードを後続節（successor）と呼ぶ．

# 第６回講義資料参考
## 有限オートマトン
- オートマトンとは，自動機械のことを意味する．計算
機科学の世界では，計算の各過程を状態とし，入
力に従って状態から状態へ遷移する仮想的な計算
機械のことをさす．
- 有限オートマトンの種類
  - 非決定性有限オートマトン（NFA:non-deterministic finite automaton）
    - εによる遷移を許すものがある．εは空語と呼ぶ．これは文字数“０”で構成される空語を含めることを意味する．
  - 決定性有限オートマトン（DFA:deterministic finite automaton）
    - 現在の状態に対し，現在の入力によって次の状態が一意に決まるものをさす．

## 状態遷移図
- 状態遷移図（state transition diagram）とは，オートマトンの各状態をノードとし，あるノードから別のノードへの遷移を有向辺で示したもの．
- 非決定性のオートマトンを表す状態遷移図
  - ある状態から別の状態への辺が複数ある場合、同じラベルをもつものが存在してもよい．
- 決定性のオートマトンを表す状態遷移図
  - ある状態から別の状態へ向かう辺が複数あった場合、同じラベルは存在しない．．

# 第７,8回講義資料参考
## 構文解析
-  構文解析とは，字句（トークン）の並びが文法に合っているかを調べること．
-  コンパイラでは，構文解析を行う機構を構文解析器（parser）と呼ぶ．
-  構文解析の方法には，「上向き型」と「下向き型」がある．
  - 上向き構文解析（bottom up parsing）
    - LR構文解析，演算子順位構文解析
  - 下向き構文解析（top down parsing）
    - LL構文解析，再帰的下向き構文解析
    - 下向き構文解析の問題点
      - 後戻り(バックトラック)
      - 左再帰性の問題
    
# 第9回講義資料参考
## LR構文解析～上向き構文解析
- LR(Left to right, Right parse)構文解析
  - 上向き構文解析のひとつ
  - yaccの解析で利用
  - スタックオートマトンと呼ばれるスタックを用いたオートマトンで表現
  - 「シフト」と「還元」の動作で解析を実現
  - LR構文解析表が必要になる(p.79参照)
    - action表： 次の動作を決める
    - goto表： 動作が還元の時につぎの状態を求める
    
# 第10回講義資料参考
## 閉包
- 生成規則が適用可能な項の集合または解析の状態
- 生成規則が適用可能な項はこの集合の外にはない
- スタックには非終端記号へと変換される途中の構文要素が格納されるため、格納する段階を区別する必要あり

## 還元の扱い
- 還元の扱いに関する注意点
  - 構文解析時の入力は，わからない
  - 求めた閉包の中には，注視点が生成規則の末端にある項が含まれる
    - → 生成規則の右辺の解析が終了
  - 生成規則の右辺の解析が終了
    - → 左辺の構文変数に還元する条件が整った項
- 還元する判断基準
  - SLR（単純LR）構文解析：解析能力小，解析表小
  - 正順LR構文解析：解析能力大，解析表大
  - LALR（先読みLR）構文解析：解析能力中，解析表中
