# Do not copy

AI 寫 code 前會先查這份清單。列在這裡的路徑，不能當範本照抄，要改用「Use instead」那一欄。

規則：
- 只有人可以修改這份清單。AI 只能在回覆最後一行提出建議：`Proposed for do-not-copy: <path>, <reason>, <what to use instead>.`
- 每一列都要有實際案例（哪次 review、哪個 bug）才加，不憑感覺加。
- 舊寫法重構完，記得把那一列刪掉。

| Path | Why not | Use instead |
|------|---------|-------------|
| src/legacy/api.ts | No error handling, swallows failures | src/lib/http.ts |
