# How SRE Relates to DevOps
## Background on DevOps
### No more silos
- Devs と Opsを分けないことという文脈 (*silos は silo ITとかでググろう）  

### Accidents Are Normal
- Accidentはミスから生まれるものではなく、むしろコンティンジェンシープランを用意できなかった結果
- よくあるパターンは、”ミスをした人”にフォーカスすること
- アクシデントを防ぐことよりも、早いリカバリを行う・行えるようにすることにフォーカスすべきである。

### Change Should Be Gradual
- 変更はリスキーであるが、変更できるくらいコンポーネント/パイプラインを小さくしないとダメ
- この変更は、小さい変更の自動テストとバグをロールバックできる仕組みを持つことで適切に行われる

### Tooling and Culture Are Interrelated
- 良いカルチャーはツールをカバーする
- ツールより組織文化を強く支持する

### Measurement Is Crucial
- 計測することで、何が起こっているか把握できる
- 計測することで、リカバリを確認できる
- 多部署との合意形成に利用できる

## Background on SRE
- SREは役割であり、実践であり、その実践のための信念である。

### Operations Is a Software Problem
- 基本的なSREの教え - operationはソフトウェアの問題である。
- なので、SREは問題解決手段としてソフトウェアエンジニアリングでの解決を行うべき。
- この考えをすべて〜プロセスからビジネスの変化〜に適用する

### Manage by Service Level Objectives (SLOs)
- SREは100%の可用性を狙わない。
- 100%は誤った目標である、プロダクトチーム、SREはユーザーに基づいた適切な可用性を選択する。
- 目標はビジネスの観点とも強く結びつく。
- SLOには文化的な意味合いもあります。SLO違反はチームを解散させる指標になります。

### Work to Minimize Toil
- SREは命令された手作業を嫌います。
- 機械が "できる" ことを、機械が "すべき" と勘違いすることはよくある。
- Googleでは、Toilは仕事とみなさない。
- プロジェクトのための時間とは、サービスの信頼性、スケーラビリティを上げるために使った時間。Operational time ≠ プロジェクトのための時間
- とはいえ、運用とは、"The Wisdom of Production" である。サービス運用における意思決定に必要な情報を提供する。
- However, if you find yourself in a position of operational underload, you may need to push new features and changes more often so that engineers
remain familiar with the workings of the service you support.

### Automate This Year’s Job Away
- toilにかけられる時間に制限がかかっている。永続的な価値を生み出すエンジニアリングの基準としては50%である。
- 50%を制限ではなく、エンジニアリングベースのアプローチを取るための保証と考える。

### Move Fast by Reducing the Cost of Failure
- SREの利点は、プロダクト開発のimprovementとしても存在する。
- 共通的なエラーのMTTR（ググってください）を減らし、プロダクト開発のベロシティを上げる。
- SREの担当領域として、問題の発見を早くし、会社全体に貢献する。

### Share Ownership with Developers
- SREは実装上の問題を解決するよりも、productionの問題解決に集中する。
- そのアプローチ・知見を製品開発チームと共有する。
- SREは、availability, latency, performance, efficiency,
change management, monitoring, emergency response, and capacity planning of the
serviceの専門知識を持っている。

### Use the Same Tooling, Regardless of Function or Job Title
- たくさんのツールを持たない。ツールがあればあるほど、一つのツールに対するの改善の効果は下がる。

## Compare and Contrast（DevOps/SRE）
- 改善のための変更を行う。
- コラボレーション=DevOps。SREはオーナーシップのシェア、パートナーを組むという関係。(で、結局よくわかってない。。。
- 変更の単位をより小さく、継続的に、自動化されたテストでという観点では共通。だが、SREでは特に、変更と信頼性のインタラクションを重要視する。
- お互いに計測大事、SREにおいてSLOはすべての意思決定に関わる
- 非難のないpost-mortemを行う。
- Devops/SREにとって良いベロシティは結果に繋がる。
- DevOps/SREは共通点多い。だけど重要な違いがある。DevOpsは文化、主義にまで及ぶが、SREはより狭義である。

## Organizational Context and Fostering Successful Adoption
- DevOps/SREのコンセプトは大きいので被るところも多い。実装によって最大の利益を得ることが条件である。（訳に自信なし）
- そこに重きをおくならビジネスの利益とインセンティブを考慮する必要がある。

### Narrow, Rigid Incentives Narrow Your Success
- 多分、SRE・DevOpsにおいては、商用運用の許可を与えて、問題をガンガン解決してもらおうということ、そして、それが、伝統的なソフトウェア開発の問題を解決するであろう。みたいな内容なのではなかろうか。

### It’s Better to Fix It Yourself; Don’t Blame Someone Else
- 他のチームを非難すんな、自分で直せ。多分上の文脈から来てると思うが。
- 開発とOpsを分けることは昔からのソフトウェア開発の課題である
- 代わりに、これらを実践してみようではないか。
	- エンジニアがソース、設定を変更するのを許可するのではなく、奨励する。開発チームがミッションにおいてその行動が制限され、その範囲内で変更ができるようにする。こうすると早くなる。
	- 非難なきpost-mortemを行う。すると問題を隠すとかの方向に行かなくなる。
- うーむなんかよくわからん文章。

```
Allow support to move away from products that are irredeemably operationally difficult. 
The threat of support withdrawal motivates product development to fix issues
both in the run-up to support and once the product is itself supported, saving everyone time. 
What it means to be “irredeemably operationally difficult” may differ
depending on your context—the dynamic here should be one of mutually understood
responsibilities. 
Pushback to other orgs might be a softer, “We think there are highervalue
uses of the time of people with this skill set,” or framed within the limit of,
“These people will quit if they’re tasked with too much operational work and aren’t given the opportunity to use their engineering skill set.”
```

### Consider Reliability Work as a Specialized Role
- プロダクト開発はSREチームの成功と関係を持つ。SREはプロダクト開発の成功と関係を持つ。
- 20人チームで１プロダクトならDevOpsのスタイルで回せるがより成長するためにはSREが必要である。

### When Can Substitute for Whether
- 組織や製品が拡大した時はサポートの優先順位、優先順位のつけ方を決める。
- GoogleではSREと開発のパートナーシップが重要であることが証明されている。
- サポートを撤回また供給するという決定は運用に関する客観的データに基づいて行われる。（ここがない）
- 効率的なSREとプロダクト開発の関係は、製品がreadyになる前に出荷されるというアンチパターンを回避させる。

### Strive for Parity of Esteem: Career and Financial
- チームメンバーは大体おんなじメソッドで評価され、同様の給料になるべき。





