# 拓展阅读：CF（进位/借位）与 OF（溢出）英文入门资料
> 用途：课后补充视角。**原则：真题优先**，这些只在有空/卡住时看，别用"看文章"替代做题。
> 建立日期：2026-09-10（第 7 次学习）

---

## 🥇 首选（最贴合你的坑）

**1. Stack Overflow · "About assembly CF (Carry) and OF (Overflow) flag"**
🔗 https://stackoverflow.com/questions/791991/about-assembly-cfcarry-and-ofoverflow-flag/792045

- **为什么推荐**：这篇是全网讲 CF/OF 区别最干净的一篇（高赞经典回答）。
- **对应你 09-10 踩的坑**：
  - 它明确说 **CF = 把两个数当无符号看，结果的第 n+1 位（超出位宽的那一位）** → 就是我们的"借位"。
  - 它明确说 **OF = 把两个数当有符号（补码）看，结果能不能被装回去** → 就是我们的"范围法"。
  - 它把 **减法 CF** 讲成"借位（borrow）"，解释了两负相减为什么不借位。
- **读法建议**：只读高赞回答那几段，10 分钟足够；重点看它对 `SUB` 和 `CMP` 的举例。

**2. Stack Overflow · "Flags of Signed and Unsigned Numbers"**
🔗 https://stackoverflow.com/questions/74641250/flags-of-signed-and-unsigned-numbers

- **为什么推荐**：短，直击"同一个位串，signed/unsigned 两种读法 → 决定用 CF 还是 OF"。
- **对应你的坑**：你 08-31 曾把"有符号/无符号"选错；这篇把"**同一次运算，两条尺子**"讲得很直白。

---

## 🥈 备选（想系统看）

**3. 王道 a86 教材 · Execution Model（英文版 CS 教材里的 FLAGS 章节）**
🔗 https://cmsc430.github.io/a86/Execution_Model.html

- 完整讲 EFLAGS 寄存器里 CF/PF/AF/ZF/SF/OF 各是什么，术语最规范（适合以后读英文手册）。

**4. Hawaii 大学讲义 · "Flags and Arithmetic"（课件）**
🔗 http://www2.hawaii.edu/~esb/2000spring.ics331/apr17.html

- 幻灯片式，带真值表，适合扫一眼看"加法/减法后各标志怎么变"。

---

## 📌 中文对照（一句话速查）

| 标志 | 英文说法 | 用哪把尺子 | 判据 |
|---|---|---|---|
| **CF** | Carry Flag / **borrow**（减法） | **无符号** unsigned | 无符号被减数 < 减数 → CF=1（借位） |
| **OF** | Overflow Flag | **有符号** signed（补码） | 结果超出 −2ⁿ⁻¹ ~ 2ⁿ⁻¹−1 → OF=1 |

> 口诀：**CF 是无符号的事，OF 是有符号的事；一次运算，两条尺子。**

---

## ⚠️ 提醒
- 英文资料里常见的 `CF = 1` 在减法中叫 **borrow**，中文叫"借位"，是同一个东西。
- 别被 x86 的 `CMP`/`SBB` 细节带偏——**你最需要的是"哪把尺子"这件事**，其他 408 不考。
