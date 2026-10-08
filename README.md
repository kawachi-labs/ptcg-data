# ptcg-data

ポケモンカードゲーム関連アプリで使う、公開してよいデータ置き場。アプリは利用者の操作時に
`raw.githubusercontent.com` から JSON を取得する。利用者の情報や戦績は置かない。

## deck-types/ja.json

日本の環境のデッキタイプ（アーキタイプ）の一覧。デッキ登録でデッキタイプを選ぶ候補に使う。

| 項目 | 内容 |
|---|---|
| `schemaVersion` | 形式の版。項目を増やすだけなら上げない |
| `updatedAt` | 一覧を更新した日（YYYY-MM-DD） |
| `deckTypes[].id` | アプリ内で使う固定の ID。**一度公開したら変えない・使い回さない**（記録の集計に使う） |
| `deckTypes[].ja` | 表示する日本語名 |
| `deckTypes[].en` | 英語名（Limitless の表記） |
| `deckTypes[].limitlessId` | Limitless のデッキ ID（`https://limitlesstcg.com/decks/<id>`）。まだ載っていなければ `null` |
| `deckTypes[].icons` | 表示するポケモンのドット絵のキー（例：`rayquaza-mega`）。National Pokédex Icon Dex 由来の素材で、キーは Limitless のアイコン名に合わせる。アプリに同梱していないキーは、アプリの更新までは代わりの表示になる |

並び順はアプリの選択肢の順になる（使われている順を目安にする）。

### 追加・変更のしかた

- 日本で先に出たデッキタイプは、Limitless に載る前でも `limitlessId: null` で追加してよい。載ったら ID を足す
- `icons` は表示に使うドット絵のキー。新しいキーを使う場合は、アプリ側の同梱素材にも追加する
- 呼び方を変えるときは `ja` だけを直し、`id` は変えない
- 使われなくなったデッキタイプも、過去の記録のために消さずに残す

初版の一覧は Limitless（`format=standard-jp` 直近12か月と、海外スタンダード直近3か月）の上位から作った。
日本語名は初期案で、見直してよい。
