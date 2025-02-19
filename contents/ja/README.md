# AIネイティブ開発ガイド

AIネイティブ開発ガイドへようこそ!
こちらは AI-Native Development Community が運営するコミュニティドキュメントです。
このドキュメントでは、GitHub Copilot などをつかった AI ネイティブ開発におけるベストプラクティスを特定の形式でまとめて、簡単に理解、評価、そしてあなたの状況に適用できるようにしています。
いくつかのものはパターンとして、名前をつけてまとめています。もし気に入れば、[GitHubのリポジトリ](https://github.com/AI-Native-Development/docs)のスターやコントリビューションをお待ちしています！どんな小さな貢献でも大歓迎です。一緒にAI-Native Developmentの方法を開拓していきましょう！

<img align="right" src="../../top.png" title="AI Native Development Guide" width="30%">

このパターンのいくつかは個人の環境で試され、効果を確認しているものの、実際のチームの環境での有効性が試されていないアイデアベースのものもあります。
ぜひ GitHub Issues にコメントをお寄せください。さまざまな議論が行われ、AIネイティブ開発の知識が共有されることを楽しみにしています。

この序文では、AIネイティブ開発とは何か、パターンとは何かについて説明します。
すでにあなたの会社でAIネイティブ開発を実践しており、このドキュメントに経験を寄稿したい場合は、ぜひあなたの貢献を歓迎します！

現在、以下の言語に対応しています：[英語 🇺🇸](https://ai-native-development.gitbook.io/docs/)、[ドイツ語 🇩🇪](https://ai-native-development.gitbook.io/docs/v/de/)、[スペイン語 🇪🇸](https://ai-native-development.gitbook.io/docs/v/es/)、[フランス語 🇫🇷](https://ai-native-development.gitbook.io/docs/v/fr/)、[イタリア語 🇮🇹](https://ai-native-development.gitbook.io/docs/v/it/)、[日本語 🇯🇵](https://ai-native-development.gitbook.io/docs/v/ja/)、[ポルトガル語 🇵🇹](https://ai-native-development.gitbook.io/docs/v/pt/)、[中国語 🇨🇳](https://ai-native-development.gitbook.io/docs/v/zh/)。

{% hint style="info" %}
この『AIネイティブ開発ガイド』のドキュメントはまだ完成版ではなく、リンク切れや誤字脱字、その他のエラーがあるかもしれません。改善にご協力いただけると幸いです。このドキュメントに貢献する方法をご覧ください。
{% endhint %}

## AIネイティブ開発とは

AIネイティブ開発とは、AIとの協業を前提とした開発プロセスや文化を取り入れることで、ソフトウェア開発を加速させるアプローチです。
AIネイティブ開発においては、GitHub Copilot や ChatGPT のような AI技術を活用することで、従来のソフトウェア開発プロセスを大幅に効率化し、革新的なソリューションを生み出すことを目指しています。

* 高速なコード補完や提案: AIツールは、開発者が入力したコードに基づいて、関連性の高いコードスニペットや関数を自動的に生成し、提案します。これにより、開発者はコードを迅速に記述し、一般的なコーディングエラーやバグを回避できます。
* 自然言語での相談: AIツールは、自然言語での質問や指示に応じてコード生成や解決策の提案ができます。これにより、開発者はプログラムの意図や機能を簡単に伝えることができます。

一方でAIネイティブ開発の導入により、開発スタイルが従来の方法から大きく変化することにも言及する必要があります。
AI技術の活用によって多くの利点が得られますが、開発者やチームがこれらの変化に適応するためには、以下の点に注意する必要があります。

* 学習と適応: AIツールや技術を効果的に活用するためには、開発者はこれらのツールの使い方や特性を学習し、適応する必要があります。これには、ツールの基本操作やベストプラクティスを習得するだけでなく、開発プロセスに組み込む方法や、チーム間での連携方法も理解することが含まれます。
* コミュニケーションスタイルの変化: AIネイティブ開発では、開発者は従来のコード中心のコミュニケーションから、自然言語を用いたコミュニケーションにシフトすることが求められます。これにより、開発者はプロジェクトの意図や要件を明確に伝えるための新たなスキルを習得する必要があります。ドキュメントはAI が読みやすい形で提供される必要があり、従来型の PowerPoint や Excel から Markdown などのファイルタイプにシフトします。
* チームの役割と責任: AIネイティブ開発の導入により、開発者やチーム内の役割や責任が再定義されることがあります。これにより、開発者は自分の専門分野や役割において柔軟性を持ち、チーム内でのコラボレーションを強化する必要があります。開発者は、AIツールの活用によって自動化されるタスクに対して、より高度な問題解決や戦略的な意思決定に集中することが求められるでしょう。

AI を開発の中に適切に取り入れることで、開発者とチームはプロダクト/プロジェクトの品質と効率を向上させることができるでしょう。
このガイドがあなたが AIネイティブ開発の入り口に立つきっかけになれば幸いです。

## パターンとは

パターンとは、特定のコンテキスト内で問題に対する繰り返し可能な解決策を記述する方法です。
AIネイティブ開発におけるパターンには、開発者およびチームが、高速なプロダクト開発のために、どのように AI を活用したら良いのかのアイデアが掲載されています。
パターンは、タイトル、問題の説明、コンテキスト、影響要素、解決策といった主要なセクションに分かれています。
パターンの形式は、実証済みの解決策を記述するのに役立ちますが、まだ確立されていないパターンについて新たな解決策をブレインストーミングする場合にも使用できます。
これは、パターンの構造が問題に対して構造化された方法で考えるための枠組みを提供するためです。

現段階でパターンの多くはまだ未成熟です。ぜひパターンを試していただき、フィードバックをお待ちしています。
また、あなたが新しいパターンを見つけたのであれば、ぜひ GitHub Issues でお知らせください。貢献をお待ちしています！

## ライセンス

![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)

AI Native Development Guideline is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International](http://creativecommons.org/licenses/by-sa/4.0/) License.
