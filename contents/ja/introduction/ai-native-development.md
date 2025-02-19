# AI-Native Documentation

GitHub Copilot のような AI 技術の活用により、開発者チーム内のエンジニアの作業が変わることは、最終的にはアーキテクチャにも影響をもたらす可能性があります。
このドキュメントでは AI ネイティブの開発手法がもたらす可能性がある影響について説明します。

## コンテキストがすべて

GitHub Copilot を代表する AI 技術が開発環境や開発プロセスに入ってくると一口に言ってもさまざまな分野があります。
開発者チームはさらなる開発スピードのためにコンテキストをより意識する必要が出てきます。
その際に注意すべきことは、あなたのプログラムにはどのような技術的なコンテキストとビジネス的なコンテキストが含まれているのかということです。
これは実は新しいトピックではなく、昔から言われていたことでしたが、AI の登場によって、開発者が強力にブーストされるようになった今、改めてその文脈で二つのコンテキストについて考えるのは価値があることでしょう。
これらのコンテキストはアーキテクチャや、エンジニアのキャリアに影響します。

また、どのコンテキストにもハイコンテキストな領域とローコンテキストな領域があります。
たとえばコーディングにおいて、単純作業を繰り返したり、誰が書いても最終的にはその処理に辿り着くと言った具合の処理を書くことはただ単に GitHub Copilot が提案することに対してタブキーを押していくだけで十分かもしれません。
一方で、高いコンテキストが必要になる領域においては、タブキーを押すだけでは何も生まれません。
この領域は経験や特定の技術領域に関する知識が求められる領域であるため、簡単に習得できるものではありません。

### 技術的なコンテキスト

技術的なコンテキストを考えるために幾つかのプログラミング言語を考えてみましょう。
Pythonのようにあるひとつのことを書く時の表現方法がある程度共通化される言語もあれば、Rubyのようにひとつのことを書くにも多様な表現が可能な言語も存在します。
また、スコープの広さも問題となります。
BASICのようなグローバルスコープが基本となる言語もあれば、狭いスコープを持つ言語も多く存在します。
また、Rustにおける参照と借用の仕組みなどは、技術的に高いコンテキストを含む典型的な例です。
さらにフレームワークレベルではさらにそのコンテキストが多段に積み重なることがあります。

### ビジネス的なコンテキスト

ビジネスドメインに関しても同様です。
データベース言語であるSQLを考えてみます。
AIは単純な作業が得意で、SQLの定型的な表現を複製するような実装には非常に向いています。
シンプルなアプリケーションの実装でデータベースへのアクセスを定義するのであれば、 コンテキストが少なくてすみます。
しかし、複雑に絡み合った巨大なデータベースを取り扱う場合、AIが生成したコードが他の処理に影響を及ぼさないことに自信を持つことは難しいでしょう。
全体的なアーキテクチャを理解し、実際のロジックについてある程度の知識が必要になるかもしれません。
テストに関しても同様で、AIは与えられたシナリオに沿ってテストを書く作業が得意ですが、網羅的なテストシナリオ自体を考えるのは難しいでしょう。
単純な CRUD 機能を持つ REST API に対する API テストは容易に書けますが、例えば認可の条件を複雑に持っているアプリケーションに関するテストを AI が完璧に書くのは難しいでしょう。

## AI-Native アーキテクチャ

さて、あなたの管理する機能/アプリケーションのアーキテクチャには、どの程度のコンテキストが存在するのでしょうか。
アーキテクチャに多くのコンテキストが含まれている場合、AI を活用した開発速度は低下する可能性があります。
なぜならば、LLM が理解できるコンテキストは限られており、大量のコンテキストを同時にAIに提供することはできないからです。
それは与えられるトークン数の上限があることも理由ですが、一般的に人間がすべての情報をAI可読性がある形で文章として提供できないことにも起因しています。
AIはある意味で、プロンプトが提供され続ければ無限に働くことができます。
一方で、人間が AI にプロンプトを与え流ことのできる時間は限られています。
その場合、開発におけるボトルネックは人間になります。
そのため人間がなるべく広いコンテキストをAIに与えずとも、AI が正しいプログラムを書けるように、機能やアプリケーションが持つコンテキストを少なくすることを検討すべきです。

サービスを小さいレベルまで分割して、疎な関係にするのは良いアイデアです。
一方で私が言及しているのは、Kubernetes の文脈におけるマイクロサービスにしようと言っているわけではありません。
SOAやライブラリレベルでの分離を含む、あなたが考えるどんな設計でも構いません。
重要なのは、コンポーネントをシンプルでテスト可能な単位に分割しておくことです。
アプリケーションが多くのコンテキストを持つほど、AIのサポートを得にくくなります。

プログラムの扱う適切なサイズについては、時々宗教戦争が起こることがありますし、AIを使った開発はまだ始まったばかりで正確な答えは存在しません。
しかし、エンジニアの生産性を最大化してプロダクトを最短で成長させることを考えると、あなたのチームでも一度 GitHub Copilot を前提にした開発手法やアーキテクチャを考えてみるのが良いでしょう。

しかし一方で、間違ってはいけないのはITアーキテクチャは "エンジニアの生産を最大化すること" が目的で考えられるべきではないということです。
あくまでもエンジニアリングは最終的に達成することのための手段として存在します。

皆さんがこの分野で積極的に議論に参加してくれることを期待しています。

## エンジニアとしてのキャリアの展望

これまでに、AIがアーキテクチャや開発文化に変化をもたらす可能性について触れてきました。
ここで、エンジニアリングのキャリアにも目を向けることが重要です。
これは、エンジニア自身だけでなく、マネージャーや組織を構築する立場の人々にとっても考慮すべき点です。

結局のところ、エンジニアは幅広いビジネス・プロダクトの知見を持つエンジニアを目指すのか、技術的に高度なエンジニアを目指すのかを考えていく必要があります。
しかし、問題はそれらの二つにおいても低コンテキストと高コンテキストの領域があることです。

たとえばコーディングにおいて、単純作業を繰り返したり、誰が書いても最終的にはその処理に辿り着くと言った具合の処理を書くことはただ単に GitHub Copilot が提案することに対してタブキーを押していくだけで十分かもしれません。
一方で、技術的なコンテキストやビジネス的なコンテキストのセクションで指定した領域は高いコンテキストが必要になる領域です。
この領域は経験や特定の技術領域に関する知識が求められる領域であるため、簡単に習得できるものではありません。
それがインターネットで手に入る知識であれば、まだキャッチアップのしようがありますが、一方で特定の組織に閉じられた知識領域で、それがしかもドキュメンテーションされていない場合、もしくは情報の入手に非常に高いコストがかかる場合はキャッチアップするのが難しいのです。

これはコーディングに限ったことではありませんが、AI は知識と経験が豊富な人間をより強化する傾向にあります。
これは上級者が新人の仕事を失ってしまうことを意味します。
それを放置すると、新人は組織における重要な仕事をすることなく、スキルの成長も見込めないことになります。
上級者のスキルはさらに上がり、組織としてその人たちの維持が難しくなることが予想され、また上級者が時間的な制約でできない退屈な作業しかしていない新人を会社に縛り付けておくことも難しくなります。

ではどうするのか、そのひとつの答えはプロダクトや組織における技術的な情報やビジネス的な情報を、コンテキストを含んだドキュメントとしてまとめあげ、社内で育てることです。
多くの人がそれらのドキュメンテーションの作成に参加して共創が起こると、企業としての知のデータベースが出来上がっていきます。
いまこそオープンソースにも似た社内コラボレーションをする機運なのです。

## チェックリスト

- [ ] あなたのプロジェクトやプロダクトはどのようなコンテキストがありますか？コンテキストを整理してみましょう。
- [ ] その文脈は一部の人のみに独占されたものですか？チームで共有されていますか？
- [ ] あなたのプロジェクトやプロダクトにおけるコードは AI がローコンテキストでも理解できるコードが多いですか？もしはいコンテキストなコードが多い場合はどのように AI が書きやすいコードに変換していきますか？
- [ ] 社内コラボレーションを促進していますか？していない場合は、チーム内やチーム間のコミュニケーションや知識共有を向上させるアクションを考えましょう
- [ ] あなたのチームのエンジニアの AI 時代のキャリアパスに関する話し合いはされていますか？ 技術的・ビジネス的などの領域を強めたいのかを話し合いましょう
