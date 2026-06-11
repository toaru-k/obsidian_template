---

---

## 管理方針
### status
todo / doing / done

### `heart`
感情的な面白さ。どれだけ笑えたか、楽しめたか、興奮したか。fun.

目安は以下。

	50: 見なきゃ人生損してる。
	40: 面白い。積極的におすすめしたい。
	30: 普通に面白い。
	25: 平均。普通。
	20: 総じて面白くない。
	10: どこを切り取っても面白くない。
	0: 絶望的に面白くない。多分この作品にこの要素を求めること自体が間違ってる。

### `head`
知的な面白さ。どれだけ新たな視点が得られたか、考え方が変わったか。interesting.

目安は `heart`のものを参照。


## ギャラリー
```base
formulas:
  total score: if ( head, head + heart + " = " + heart + " + " + head, "-" )
properties:
  formula.total score:
    displayName: score
views:
  - type: cards
    name: ギャラリー
    filters:
      and:
        - file.tags.contains("media-note")
        - file.folder.startsWith("📕Media Notes")
    order:
      - title
      - summary
      - formula.total score
    sort:
      - property: start_date
        direction: DESC
    image: note.cover
    imageFit: contain
    cardSize: 300
    imageAspectRatio: 1
  - type: table
    name: ランキング
    filters:
      and:
        - file.hasTag("media-note")
        - file.folder.startsWith("📕Media Notes")
    order:
      - title
      - type
      - summary
      - formula.total score
      - status
      - start_date
      - finish_date
      - tags
    sort:
      - property: formula.total score
        direction: DESC
      - property: heart
        direction: DESC
      - property: head
        direction: DESC

```