## Chinese Ngrams Counts 

平时学习和做研究，有时候需要用到中文Ngrams和单词频率统计数据库，但在网上一查，却很少有这方面的现成资料。所以就想着自己跑下中文的语料库，抓取这些特征，并且分享出来。目前我只在清华大学的[THUCNews](http://thuctc.thunlp.org/#获取链接)上做了尝试。之后可能还会添加其他语料库的Ngrams和单词频率统计的信息。


## 语料库预处理
### 文本处理
1. 我将所有多余的空格，包括分行，都移除掉了。
2. 单个或者连续的字母，都被替换为L，表示Letter(s)。
3. 单个或者连续的数字，都被替换为D，表示Digit(s)。

### 语料清洗
由于THUCNews总共有836,076文件，所以我移除了字符串数低于1000的文件，另外由创建了一个次级语料库，方便后面提取4-gram和5-gram信息。THUCNews原语料库和次级语料库的基本统计数据如下：

|  | 原语料库 | 次级语料库 | 
| :---: | :---: | :---: |
| 文件数 | 836076| 269622 |
| 字符数 | 716796576 | 458822610 |


不过要注意的是，在提取Ngrams时，当N小于等于3时，我对原语料库和次级语料库都做了Ngram的提取分析。


## Nrams的抓取和统计
### 基本方法
- 分文件统计。每个文件的Ngram都重新统计一次，最后合并计算。显然一个文件的结束不代表另外一个文件的开始，所以我并没有先将所有的文件都合并在一起，再集中统计Ngram信息。
- 不清洗标点符号。统计标点符号，可用于文本生成。如果不需要标点符号，可以简单地在ngram文件中将含有标点符号的ngram移除掉 -- 这样实际上还增加了ngram的准确度，因为标点符号前后的文本，显然没有直接的相关性，我们不能直接把它们合并在一起（移除掉标点符号），再算ngram。如果这前后的文本有倾向性，那么这个ngram统计就会有偏差和bias。

### 4-和5-gram的提取
受限于计算机的性能，我的电脑（Mac pro 2017）无法一口气统计完语料库中的4-gram和5-gram的频率信息，所以我采取了分步统计的估计方法：
<br>**第一步**：对于4-gram，我把次级语料库分成了三个部分：1. 体育, 娱乐, 家居, 彩票, 房产; 2. 教育, 时尚, 时政, 星座, 游戏;3. 社会, 科技, 股票, 财经。对于5-gram，我把次级语料库分成了四个部分：1. 体育, 娱乐, 家居, 彩票, 房产; 2. 教育, 时尚, 时政, 星座, 游戏; 3. 社会, 科技; 4. 股票, 财经.
<br>**第二步**：抓取并统计了每个部分语料库的4-或5-gram信息，并移除掉那些频率只有1的ngram。
<br>**第三步**：合并各个部分统计出的4-或5-gram信息。




## 统计结果
THUCNews统计结果：https://drive.google.com/drive/folders/1zq4-bTKj7H8q1wuJV8XfJV1rqvrGOXo8?usp=sharing
### 须知
- 文件名中带有full的，表示的是原语料库的统计信息。
- 对于trigram及以上的ngrams，我还做了点分类工作，把频率大于10的另外统计，并且在文件上标明“>=10"。
- “words.txt”是用结巴分词统计出来的结果。
