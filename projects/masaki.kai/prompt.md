# グラフィックレコーディング (グラレコ) HTML 作成プロンプト V3.1

以下の要件に従って、グラフィックレコーディングを HTML で再現してください。
## グラフィックレコーディングとは
グラフィックレコーディング（グラレコ）とは、会議やプレゼンテーションなどの内容を図やイラスト、文字を使ってリアルタイムにまとめる手法です。議論の全体像を把握しやすくなり、アイディアが出やすくなるメリットがあります。文字だけの議事録と比べて直感的に伝わりやすく、視覚的な記録は情報の記憶に残りやすいという特徴があります。

## 基本要件
- 手書き風フォントを使用（Kaisei Decol, Yomogi, Zen Kurenaido）
- 絵の代わりに Font Awesome アイコンや絵文字を使用
- 下記のSVGアセットは例外的に使用可能（積極的に使用して）
- カードは背景を透明にし、枠は使用せず、背景になじむようにする
- 手書き風の吹き出しを CSS で表現（背景は薄い透明度に）
- レスポンシブデザイン
- 5カラム構成（コンテナ幅は2000px）
- カード間の間隔を広くとる（40px程度）
- グリッドのギャップは30px
## タイポグラフィ
  - タイトル：32px、グラデーション効果、太字、Font Awesomeアイコンを左右に配置
  - サブタイトル：16px、#475569、関連するFont Awesomeアイコンを添える
  - セクション見出し：18px、# 1e40af、左側にFont Awesomeアイコンを必ず配置し、アイコンにはアニメーション効果
  - 本文：14px、#334155、行間1.4、重要キーワードには関連するFont Awesomeアイコンや絵文字を小さく添える
  - フォント指定：
    ```html
    <style>
    @ import url('https ://fonts.googleapis.com/css2?family=Kaisei+Decol&family=Yomogi&family=Zen+Kurenaido&display=swap');
    @ import url('https ://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css');
    </style>
    ```
## カラーパレット
```
<palette>
<color name='旅行-1' rgb='45858C' r='68' g='133' b='140' />
<color name='旅行-2' rgb='A0D9D9' r='160' g='216' b='216' />
<color name='旅行-3' rgb='D9C589' r='216' g='196' b='136' />
<color name='旅行-4' rgb='BF9765' r='191' g='150' b='101' />
<color name='旅行-5' rgb='D92B04' r='216' g='43' b='4' />
</palette>
```

## SVGアセット

1. https://raw.githubusercontent.com/furoku/svg-library/feature/initial-setup/projects/masaki.kai/resource/svg/company-as-a-collaborative-creative-environment_resized.svg
2. https://raw.githubusercontent.com/furoku/svg-library/feature/initial-setup/projects/masaki.kai/resource/svg/people-collaborating_-DAO-like-organization_-mutual-support_resized.svg
3. https://raw.githubusercontent.com/furoku/svg-library/feature/initial-setup/projects/masaki.kai/resource/svg/team-members-supporting-and-cheering-each-other_resized.svg

## CSS 主要設定
```css
.container {
    max-width: 2000px;
    margin: 0 auto;
}
body {
    /* 手書き風グリッドライン背景 */
    background-image: url('data:image/svg+xml;utf8,<svg width="100" height="100" xmlns="http: //www.w3.org/2000/svg"><path d="M0 0h100v100H0z" fill="none"/><path d="M0 10h100M10 0v100" stroke="%23e0e0e0" stroke-width="0.5" stroke-dasharray="2,3"/></svg>');
    background-size: 30px 30px;
    background-color: # f9f7f1;
    overflow-x: hidden;
}
.grid-container {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 30px;
}
.card {
    background-color: transparent;
    padding: 15px;
    border-radius: 15px;
    position: relative;
    margin-bottom: 40px;
    transition: transform 0.3s ease;
}
.icon-large {
    font-size: 70px;
    display: block;
    margin: 15px auto;
    text-align: center;
}
.speech-bubble {
    position: relative;
    background-color: rgba(242, 187, 87, 0.1);
    border-radius: 15px;
    padding: 12px;
}
.comparison-item {
    background-color: transparent;
    padding: 10px;
    border-radius: 10px;
}
.highlight-box {
    border-left: 3px solid # F2BC57;
    padding-left: 10px;
    background-color: transparent;
}
/* メディアクエリ */
@ media (max-width: 1600px) {
    .grid-container {
        grid-template-columns: repeat(3, 1fr);
    }
}
@ media (max-width: 768px) {
    .grid-container {
        grid-template-columns: repeat(2, 1fr);
    }
}
@ media (max-width: 480px) {
    .grid-container {
        grid-template-columns: 1fr;
    }
}
```
## レイアウト指示
- 手書き風の雰囲気を強調
- 重要なキーワードは大きく、補足説明は小さいフォントで
- Font Awesome アイコンやアセットを大きく使用して視覚的興味を引く
- カードは全て背景を透明にし、境界や枠線を使わない
- カード内のコンテンツ（比較項目、吹き出し、ハイライトボックスなど）も透明か薄い透明度に設定

## 作成手順
1. まず、全体構造を構築（コンテナ、タイトル、5カラムグリッド）
2. 各セクションをカードとして配置
3. カードには見出し、大きなアイコン、テキスト内容を含める
4. 比較項目や統計データは横並びで表示
5. 重要なポイントは吹き出しやハイライトボックスで強調
6. フッターにはグラフィックレコーディングの作成日と情報源を記載
## 変換するコンテンツ
AIが業務に浸透すると「この仲間と一緒にいたいかどうか」が大事になるという話

20
甲斐真樹 | イー・エージェンシー
甲斐真樹 | イー・エージェンシー
2024年12月29日 11:16
AI時代が経営にもたらす変化
AIがさらに浸透していくこれからの時代、人が担ってきた仕事の一部はAIに取って代わられるかもしれません。SNSやメディアはしきりにそんなことを煽ります。
しかし、経営者がそれを過度に解釈して「AIに仕事を奪われた人はもういらない」と捉えるのは、あまりにも短絡的な考え方だと感じています。

AIが浸透したら、むしろ人はより人間らしさが求められるともよく言いますよね。
人間らしさって、勝ち負けをシビアに振り分けることではなくて、むしろ互いを支え合い、応援し合う関係のなかでこそ育まれるものだと思います。
AIが浸透するこれからの時代だからこそ、より人間性ある経営をすべきだと私は考えてます。

スポーツの試合から学ぶチームの力
たとえば、スポーツの試合をみても、実際にピッチやコートに立っている選手だけが戦っているわけではないですよね。ベンチにいる選手、ベンチ入りできなかった選手、そしてスタンドで声援を送るファンやサポーター……。みんなが力を合わせているからこそ、「一緒に目標を目指して頑張っている」という熱さや一体感が生まれるんじゃないでしょうか。
ピッチやコートで戦っていた選手も、ベンチからの応援、ファンの声援があったからこそ、力を出せたと感じているはずです。
人が感動する場面って、必ずしも試合の勝ち負けだけではないです。選手を一生懸命に応援しているファンの涙にもらいなきをすることもありませんか？

会社もきっと同じだと思うんです。成果を出すプレイヤーがいるのはもちろん大切ですよ。でも、彼らを支えたり、応援したり、チーム全体の士気を高める人たちも、それと同じくらい大切なんじゃないでしょうか。
ともに笑い合い、励まし合いながら前に進んでいく。そういう空気感やつながりがあるからこそ、「この仲間と一緒にいたい」「この会社で仲間と目的に向かって頑張りたいかどうか」と思えるようになるはずです。

この仲間と一緒にいたいかどうか
AIが会社の業務に浸透すればするほど、私はこうした会社づくりが大切になってくるような気がしますし、それによって人が人らしく輝ける場面を増やしていくと思います。
「AIに勝てるかどうか」ではなく、「この仲間と一緒にいたいかどうか」「この会社で仲間と目的に向かって頑張りたいかどうか」が大事。
これからの時代こそ、人と人とを結びつける“仲間を応援する”という仕事も、これからますます意味を持つようになるのではないでしょうか。

業務で成果を出すことはもちろん大事ですが、そこに“応援”が加わって、一丸となって目標を追いかけている――そんな熱い仲間がそろった会社こそ、これからの時代にますます魅力的な会社だと言われるんじゃないかと思うんです。

共同創造の“器”としての会社
付け加えると、将来、会社は共同創造の器のようになっていくと思います。その時はこれまでの株式会社というよりDAOのような形態になるのかもしれません。ともに笑い合い、励まし合いながら前に進んでいく。そんな人の魅力が溢れる会社が強いんだと思います。

2025年に向けてAIの時代こそ、人間性溢れる経営が大切になると思ってます。