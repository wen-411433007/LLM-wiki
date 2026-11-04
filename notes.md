---
title: "位移電流為什麼是必要的"
type: notes
question: "位移電流為什麼是必要的？"
generated: 2026-11-04
wiki_pages: ["maxwell-equations", "electromagnetic-waves", "vector-derivatives", "vector-integral-theorems", "classical-electrodynamics"]
coverage: "部分"
status: "已確認"
---

# 位移電流為什麼是必要的

> 少了位移電流，安培定律在非穩定電流下會自相矛盾，電荷守恆不會內建在方程組裡，也推不出電磁波。

## 涵蓋程度

**部分涵蓋。** wiki 足以回答「為什麼必要」，但有兩點限制：

- 所有內容都來自單一來源 [[src-2024-griffiths-electrodynamics|Griffiths 2024]]，全書目前只讀了約 16%，沒有其他來源可以交叉比對。
- 公式是從 PDF 抽取的文字還原的，尚未對照原書版面。

## 內容

以下頁碼都是 Griffiths 2024 的書頁。

### 問題：舊的安培定律在非穩定電流下出錯

19 世紀中期的第四條方程式只有這樣（[[maxwell-equations|馬克士威方程組]]，p.335）：

$$
\nabla \times \mathbf{B} = \mu_0 \mathbf{J}
$$

它有兩個問題：

1. **和數學恆等式衝突**：旋度的散度恆為零（[[vector-derivatives|梯度、散度與旋度]]，Eq. 1.46，p.23）。對上式取散度，左邊必為零，右邊在非穩定電流下卻不為零（[[maxwell-equations|馬克士威方程組]]，p.335）。
2. **答案取決於所選曲面**：替電容器充電時，通過同一條迴路的電流會隨曲面而變，平面得到 $I$，氣泡形曲面得到零（[[maxwell-equations|馬克士威方程組]]，p.335–336）。

> [!abstract] 綜合判斷
> 這兩個問題可以看成同一件事。Stokes 定理的推論說，旋度的面積分只取決於邊界線，與所選曲面無關（[[vector-integral-theorems|向量微積分基本定理]]，p.34）。平面和氣泡形曲面共用同一條迴路，舊定律卻給出不同的結果，可見這時 $\mu_0 \mathbf{J}$ 不可能是某個向量場的旋度。

### 修正：Maxwell 加上的一項

Maxwell 用純理論的論證，在安培定律加入一項（[[maxwell-equations|馬克士威方程組]]，Eq. 7.46，p.336）：

$$
\nabla \times \mathbf{B} = \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}
$$

他把 $\mathbf{J}_d \equiv \varepsilon_0 \, \partial\mathbf{E}/\partial t$ 稱為位移電流（displacement current）（Eq. 7.47，p.337）。Griffiths 指出這個名稱有誤導性，因為它除了加在 $\mathbf{J}$ 上之外和電流無關（p.337）。

### 驗證：電容器悖論解決了

再算一次充電中的電容器。假設兩板很靠近，板間電場是 $E = \sigma/\varepsilon_0 = Q/(\varepsilon_0 A)$，所以板間 $\partial E/\partial t = I/(\varepsilon_0 A)$。修正後的安培定律寫成積分形式（[[maxwell-equations|馬克士威方程組]]，Eq. 7.48，p.337）：

$$
\oint \mathbf{B} \cdot d\mathbf{l} = \mu_0 I_{\text{enc}} + \mu_0 \varepsilon_0 \int \frac{\partial \mathbf{E}}{\partial t} \cdot d\mathbf{a}
$$

| 曲面 | $I_{\text{enc}}$ | $\int (\partial\mathbf{E}/\partial t) \cdot d\mathbf{a}$ | 右邊合計 |
|---|---|---|---|
| 平面 | $I$ | 0 | $\mu_0 I$ |
| 氣泡形曲面 | 0 | $I/\varepsilon_0$ | $\mu_0 I$ |

兩個曲面得到相同的答案，只是平面的結果來自傳導電流，氣泡形曲面的結果來自位移電流（p.337）。

> [!abstract] 綜合判斷
> 這正好符合上面提到的 Stokes 定理推論：修正之後，共用同一條迴路的兩個曲面，積分結果相同。

### 必要的三個理由

**1. 讓理論自洽，並內建電荷守恆。** 修正後，電容器悖論解決了（p.337），對方程式取散度也能得到連續方程，所以電荷守恆不是額外的假設（[[maxwell-equations|馬克士威方程組]]，p.340–341、p.362；[[classical-electrodynamics|古典電動力學]]，p.362）。

> [!abstract] 綜合判斷
> 這一步可以用 wiki 裡的式子寫出來。對修正後的方程式取散度，左邊因為旋度的散度為零而消失，再代入高斯定律 $\nabla \cdot \mathbf{E} = \rho/\varepsilon_0$：
>
> $$0 = \mu_0 \nabla \cdot \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial}{\partial t}(\nabla \cdot \mathbf{E}) = \mu_0 \left(\nabla \cdot \mathbf{J} + \frac{\partial \rho}{\partial t}\right)$$
>
> 結果正是連續方程 $\partial\rho/\partial t = -\nabla \cdot \mathbf{J}$。原本的矛盾，變成了電荷守恆。

**2. 推出電磁波。** 修正項是電磁波傳播的關鍵，少了它就得不到波動方程，也就沒有光的電磁理論（[[maxwell-equations|馬克士威方程組]]，p.337；[[electromagnetic-waves|電磁波]]，p.402）。波速是 $1/\sqrt{\varepsilon_0 \mu_0} = 3.00 \times 10^8$ m/s（Eq. 9.42，p.402）。$\varepsilon_0$ 和 $\mu_0$ 分別來自庫侖定律和 Biot–Savart 定律，是用與光無關的實驗測得的，卻能算出光速（[[electromagnetic-waves|電磁波]]，p.402）。

**3. 補上電與磁的對稱。** 變化的磁場感應電場，變化的電場也感應磁場（[[maxwell-equations|馬克士威方程組]]，p.337）。

### 實驗與爭議

- **實驗確認**：一般電磁實驗中很難偵測到位移電流，所以 Faraday 等人沒有在實驗室發現它。真正的確認來自 1888 年 Hertz 的電磁波實驗（[[maxwell-equations|馬克士威方程組]]，p.337）。
- **Maxwell 的動機**：他本人的主要動機不是挽救連續方程，而是一個後來被否定的以太模型（[[maxwell-equations|馬克士威方程組]]，p.336–337）。
- **算不算磁場的來源**：Griffiths 認為就直接作用來說它像來源，但電荷與電流才是最終的來源。書中同時列出正反兩方的文獻（[[maxwell-equations|馬克士威方程組]]，p.337 註 25）。

## 尚未涵蓋

- **物質中的位移電流**：wiki 有 $\mathbf{D}$ 和 $\mathbf{H}$ 的方程式，但沒有說明位移電流在物質中的意義。建議把 Griffiths §7.3.5 補進 [[maxwell-equations|馬克士威方程組]]。
- **安培定律與法拉第定律本身**：wiki 只在馬克士威方程組裡提到它們，沒有專頁。建議匯入 Griffiths 第 5 章和第 7 章。
- **位移電流的歷史細節與 Hertz 的實驗**：wiki 只有結論，沒有細節。可以從下方的建議參考文獻補充。

## 本文引用

**原始來源**

- [[src-2024-griffiths-electrodynamics|Griffiths 2024]]：Griffiths, D. J. (2024). *Introduction to Electrodynamics* (5th ed.). Cambridge University Press.

**用到的 wiki 頁面**

- [[maxwell-equations|馬克士威方程組]]
- [[electromagnetic-waves|電磁波]]
- [[vector-derivatives|梯度、散度與旋度]]
- [[vector-integral-theorems|向量微積分基本定理]]
- [[classical-electrodynamics|古典電動力學]]

## 建議參考文獻

這份清單沿用第一版的搜尋結果。第二版的內文只多了 wiki 新增的電容器例子，沒有用到這些文獻。我只確認過文獻的身分和連結，還沒有詳讀內容。

| # | 文獻 | 下載 | 建議存放 | 能補的缺口 | 查核日期 |
|---|---|---|---|---|---|
| 1 | MIT OCW，8.022 Physics II（Fall 2004），Lecture 19 講義。公式用 Gaussian 單位。 | [下載 PDF（121 KB）](https://ocw.mit.edu/courses/8-022-physics-ii-electricity-and-magnetism-fall-2004/ece8a047519660f7128c2dea6fcec74d_lecture19.pdf) | `raw/articles/` | 電容器例子的第二個來源，可以和 Griffiths 交叉比對 | 2026-11-04 |
| 2 | University of Edinburgh，EM 3 講義，Section 12: The Displacement Current。 | [下載 PDF（78 KB）](https://www2.ph.ed.ac.uk/~mevans/em/lec12.pdf) | `raw/articles/` | 連續方程與電容器悖論的另一種講法 | 2026-11-04 |
| 3 | Haus, H. A., & Melcher, J. R. *Electromagnetic Fields and Energy*. MIT OCW RES.6-001（CC BY-NC-SA）。 | [下載 PDF（20 MB）](https://ocw.mit.edu/courses/res-6-001-electromagnetic-fields-and-energy-spring-2008/res_6_001_s_08coursetextbook.pdf) | `raw/books/` | 物質中的位移電流（§6.2） | 2026-11-04 |
| 4 | Maxwell, J. C. (1865). A Dynamical Theory of the Electromagnetic Field. *Phil. Trans. R. Soc.* 155, 459–512。公有領域。 | [下載 PDF（19.6 MB）](https://upload.wikimedia.org/wikipedia/commons/1/19/A_Dynamical_Theory_of_the_Electromagnetic_Field.pdf) | `raw/papers/` | 歷史細節：Maxwell 本人的論述 | 2026-11-04 |
| 5 | Hertz, H. (1893). *Electric Waves*. D. E. Jones 譯。Macmillan。公有領域。 | [下載 PDF（大小未標示）](https://iiif.wellcomecollection.org/pdf/b2172457x) | `raw/books/` | Hertz 實驗的細節 | 2026-11-04 |
| 6 | Bork, A. M. (1963). Maxwell, Displacement Current, and Symmetry. *Am. J. Phys.* 31(11), 854–859。 | [官方頁面（需付費或登入）](https://doi.org/10.1119/1.1969140) | `raw/papers/` | 位移電流的歷史。Griffiths p.337 註 24 引用，已在閱讀佇列 | 2026-11-04 |
| 7 | Kitano, M. (2023). Why the controversy over displacement currents never ends? arXiv:2311.15877。預印本。 | [下載 PDF（346 KB）](https://arxiv.org/pdf/2311.15877) | `raw/papers/` | 位移電流算不算磁場來源的爭議 | 2026-11-04 |
| 8 | Suárez, A., Martí, A. C., Zuza, K., & Guisasola, J. (2022). Cause-effect relationships in Maxwell's equations and their implications in the teaching of electromagnetism in introductory physics courses. *Rev. Bras. Ensino Fís.* 44, e20220230。 | [下載 PDF（5.4 MB）](https://arxiv.org/pdf/2204.13479) | `raw/papers/` | 同上，立場見下方說明 | 2026-11-04 |
| 9 | Heras, J. A. (2011). A formal interpretation of the displacement current and the instantaneous formulation of Maxwell's equations. *Am. J. Phys.* 79, 409–416。 | [下載 PDF（153 KB）](https://arxiv.org/pdf/1103.3529) | `raw/papers/` | 位移電流如何貢獻磁場的形式解釋 | 2026-11-04 |
| 10 | Suárez, Á., Martí, A. C., & Monteiro, M. (2025). Revisiting the displacement current: Two key examples showing when and why it can be neglected. arXiv:2502.14737。預印本。 | [下載 PDF（521 KB）](https://arxiv.org/pdf/2502.14737) | `raw/papers/` | 什麼時候可以忽略位移電流 | 2026-11-04 |

**可能與 wiki 有出入，未查證：**

- 第 8 筆主張電荷與電流才是場的來源，反對「變化的電場造成磁場」這種因果讀法。這可能與上文「變化的電場也感應磁場」的說法有出入（[[maxwell-equations|馬克士威方程組]]，p.337）。wiki 也記錄了 Griffiths 認為電荷與電流才是最終來源，所以差異可能只在用詞。
- 第 7、8、9 筆在這個爭議上的立場不完全相同。

**連結測試結果：**第 6 筆的 DOI 能導向官方頁面，網址也符合論文標題，但官方網站擋下自動測試，我沒有看到頁面內容。其餘 9 筆都確認回傳的是 PDF。

想匯入時，可以自己點連結下載後貼給 Claude，或說「匯入建議文獻第 N 筆」。
