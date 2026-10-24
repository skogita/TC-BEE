# TC-BEE — base-station-free correction of GPS broadcast ephemeris, for long-range drones — companion source for the book

Design documents and code for the system built in ***Toward a Million Lines VII — For Long-Range Drones: Developing GPS Correction Methods, Fixing Satellite Orbits Without a Base Station (TC-BEE)*** (Japanese title 『LLM で 100 万行のソフトウェア開発 VII — 長距離飛行ドローンむけ GPS の補正法の開発：基準局なしで衛星の軌道を直す』; the book has a Japanese edition and an English edition; the ZIP is common to both).

**TC-BEE** (Trajectory-Constrained Broadcast Ephemeris Error Estimation) lets a single receiver on a drone estimate and remove the orbit and clock offsets of the GPS broadcast ephemeris by itself, from observations of a long flight along lines, circles and helices, with no base station and no correction service. The repository holds three parts: the **methods layer** `src/gnsslib/` (the corrections and positioning methods of the book, each an independent part), the **TC-BEE application** `src/tcbee/` (the estimation and the run), and the **simulator and verification app** `src/bench/` (it adds errors to the observations and checks that each method removes them; the screens are Kotlin sources in `ui/`). The book also teaches all the basics of GPS, from the observations to the corrections, from scratch. In this project **the design documents are the source of the code**.

## Download

**The ZIP is on the [Releases](../../releases) page**, not in this repository. The release has one ZIP:

| File | Contents |
|:---|:---|
| `tcbee.zip` | The design documents (`docs/`, L1-L5, Japanese, the source), the code (`src/`, Python; `ui/`, Kotlin sources), the JSON schemas of the ledger (`schemas/`) and the table of the RF entered in the ledger (`requirements-spec.md`). One package for both editions of the book (Japanese and English). The EPUB of the book is not included |

The code needs Python 3.11 on your PC: `pip install numpy scipy pandas` and run from the unpacked folder, for example `python -m src.bench.sim.sim_main --case <case.json> --out <folder>` for the simulator and `python -m src.tcbee.run.core_main --config <config.json> --batch` for the main program. There is **no ready-built app and no APK**; the Kotlin screens are provided as sources only. The ledger, computation results, intermediate saves and automatically generated tests are not included, and neither is the EPUB of the book. The simulator makes the observations, so no data has to be downloaded.

You are free to change the design documents and the code and compare the results.

---

## License

- **The author holds the copyright.**
- **The code is under the GNU General Public License v3.0 or later (GPL-3.0-or-later).** The full text is [`LICENSE`](LICENSE). **If you modify it and distribute it, you must publish the source under the same GPL-3.0-or-later terms.**
- **The design documents and the text are under the Creative Commons Attribution-ShareAlike 4.0 International license (CC BY-SA 4.0).** This covers `docs/`, the READMEs and the other written text of this repository, and the text of the matching book. See [`LICENSE-DOCS.md`](LICENSE-DOCS.md).
- **If you use them, say so.** State where it came from (the title of the book and the name of this repository) and keep the copyright notice. If you changed it, say that you changed it.
- **In this project the design documents are the source of the code.** When you publish something made from this code, **publish the design documents together with the code.**
- Third-party components (numpy, scipy, pandas installed with `pip install`) remain under their own original licenses.
- Provided "as is", without warranty — as the GPL-3.0 text says.

## 著作権とライセンス

- **著作権は、著者にあります。**
- **コードは、GNU General Public License v3.0 以降（GPL-3.0-or-later）です。**全文は [`LICENSE`](LICENSE) です。**改変して配布するときは、同じ GPL-3.0 以降の条件で、ソースを公開する義務があります。**
- **設計書と文章は、Creative Commons 表示-継承 4.0 国際（CC BY-SA 4.0）です。**このリポジトリの `docs/`・README ほかの文章と、対応する本の文章が当たります。内容は [`LICENSE-DOCS.md`](LICENSE-DOCS.md) です。
- **使ったときは、使ったことを書いてください。**どこから使ったか（本の題名と、このリポジトリの名前）と、著作権の表示を、使った先に書いてください。直したときは、直したことも書いてください。
- **このプロジェクトでは、設計書がコードの源です。**コードを使って作ったものを公開するときは、**設計書も、コードと一緒に公開してください。**
- 第三者の部品（`pip install` で入る numpy・scipy・pandas）は、それぞれの元のライセンスのままです。
- 現状のまま（as is）提供します。保証はありません（GPL-3.0 の全文のとおりです）。
