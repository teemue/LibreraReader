---
layout: main
---

# TTS更换

>文本到语音替换用于更改引擎发音某些单词的方式，在阅读时跳过某些字符或设置正确的重音标记。

*启用TTS替换
*显示带有替换结果的段落
*“ **替换**”对话框，用于设置替换规则

|1|2|3|
|-|-|-|
|![](1.png)|![](2.png)|![](3.png)|

支持经典替换(将一个字符串直接更改为另一个字符串)，或者您可以使用正则表达式(RegExp)。

##表达式

*“文字”-简单文字
*“ *文本”-* RexExp规则
*“＃text”-禁用的规则
*“ text256”-禁用的规则

＃#示例

*“解放”。 -&gt;“库”-替换库。与Librera
*“ Librera”-&gt;“Libréra”-添加正确的压力标记
*“＃Lib。” -&gt;“图书馆”-使用“＃”禁用规则
*“ *(L | l)ib。” -&gt;“ $ 1ibrera”-替换Lib。与Librera和lib。与librera
*“ * [()”«»*“”/[]“-&gt;”“-跳过字符
*“ * [？！：;; – | – | ―]”-&gt;“，”-用暂停(，)替换字符

## TTS命令

*“文本”-&gt; ttsPAUSE-在“文本”之后添加暂停
*“文本”-&gt; ttsSTOP-如果在句子中找到“文本”，则停止TTS
*“文本”-&gt; ttsNEXT-如果句子中找到“文本”，则转到下一页
*“文本”-&gt; ttsSKIP-如果在句子中找到“文本”，则跳过阅读句子

##添加规则文件

**Librera**支持**@Voice Reader**的RegExp规则文件
在下面查看此示例**demo-replaces.txt**：

```
" живого " "живо́ва"
" как глаза " " как глаза́ "
" мне глаза" " мне глаза́"
" наклоняющая головы" "наклоня́ющая го́ловы"
" никакого стрелка" "никако́во стрелка́"
" ПОЖАРОБЕЗОПАСНУЮ СРЕДУ" "пожарабезопа́сную среду́."
" Стрелки!" "Стрелки́!"
" стрелки?" "стрелки́?"
", все так," ", всё так,"
"Зачем, стрелок?" "Зачем, стрело́к?"
"стрелок?" "стрело́к?"
*"(?i)\b\Q душа в душу\E\b" "душа́ в ду́шу"
*"(?i)\b\Q подогнулись\E\b" "падагну́лись"
*"(?i)\b\Q стрелки почувствовали\E\b" "стрелки́ почувствовали"
*"(?i)\b\Q стрелки продолжили\E\b" "стрелки́ продолжили"
*"(?i)\b\Q стрелку из\E\b" "стрелку́ из"
*"(?i)\b\Q стрелок\E\b" "стрело́к"
*"(?i)\b\Q стрелы\E\b" "стре́лы"
*"(?i)\b\Q*\E\b" "сно́ска"
*"(?i)\b\Q1 курса\E\b" "1-го курса"
*"(?i)\b\Q171 группы\E\b" "171-ой группы"
*"(?i)\b\Q1977\E\b" "1977-ой"
*"(?i)\b\QAcapela\E\b" "Акапэ́'ла"
*"(?i)\b\QBIOS\E\b" "БИ́“О́С"

*"(^| )(Д|д)-р" " доктор"
"(^| )(Г|г)-н" " господин"
*"(\d+)\s?-\s?я\b(?# ""я"" на границе слова)" "$1-я "
```
##跳过PDF文档中的裁剪区域
> PDF文件中的页面(书籍，期刊文章，教科书等)通常具有在整个文档中运行的页眉和页脚。您可以通过两根手指捏住跑步头，将其继续到下一页(和上一页)。但是您的TTS引擎对您的操作一无所知。因此，您需要告诉它做什么(跳过烦人的事情！)，同时大声朗读文档。

在**Librera**中，我们引入了特殊的替换项(命令)，这些替换项(命令)使您可以忽略裁切区域并确保连续无间断的读取。
*在“ **替换**”窗口中，在左列中输入一个单词或单词序列，并用_ttsSKIP_进行替换。此替换将告诉引擎跳过此单词/单词序列的句子
*在左栏中输入一个单词或单词序列，并用_ttsNEXT_代替。替换内容将告诉引擎跳过此单词/单词序列的句子，并立即转到下一页
*别忘了按_APPLY_来让补发

|4|5|
|-|-|
|![](4.png)|![](5.png)|

> **请几次测试您的更改，以确保一切正常进行！**

## 按原样阅读缩写

有时缩写 TTS 读错了，我们可以帮助它按原样阅读。
```
"*(\w). (\p{javaLowerCase})" "$1 $2"
```
