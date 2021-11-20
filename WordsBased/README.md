## BaiduKnowsNgrams (Words Based)
- 语料库：百度知道问答文本，基于这个[MiningZhiDaoQACorpus](https://github.com/liuhuanyong/MiningZhiDaoQACorpus)项目。
- 分词：使用[结巴分词](https://github.com/fxsjy/jieba)。
- 数据: 语料库有11多亿字，6.5亿个词。有大约1.5百多万的单词。
- 处理：语料库没有做任何处理，直接分词。Ngram从Unigram, 一直计算到4-gram，用的是相对频率。Unigram把所有只出现一次的词删掉了。bigram，trigram和4-gram中把所有出现次数少于6次的，都删掉，以节约内存。Ngrams里有<START>和<END>两个特别的token来记录每个ngram在句首和句尾的能力。Unigram里面有一个<UNK> token来代表所有只出现一次或者没出现的相对概率。
- 我最近一个[关于数据增强的项目](https://github.com/jaaack-wang/linguistic-knowledge-in-DA-for-NLP)，使用了这个BaiduKnowsNgrams。
- 下载：https://drive.google.com/file/d/1IA7HfpYrB5XRUPSV69DVKl2PANU5NvpH/view?usp=sharing

<hr>

- Corpus: BaiduKnows Q&A Text Corpus, based on this [MiningZhiDaoQACorpus](https://github.com/liuhuanyong/MiningZhiDaoQACorpus) project.
- Tokenizer: jieba tokenizer](https://github.com/fxsjy/jieba).
- Stat: The corpus has over 1.1 billion Chinese characters, over 6.5 million words, and over 1.5 million unique words. 
- Making: The corpus was not preprocessed. And the Ngrams contains unigram, up to 4-gram, which are calcuated using relative frequency. For efficiency concerns, I deleted all unigrams which only occur once, all other ngrams that occur less than 6 times. The ngrams comes with two special tokens, <START> and <END> to keep track of these ngrams' ability to stay ahead of at the end of a line. Unigram also has an additional token <UNK> to represent all the one-off and unseen unigrams.
- I used this BaiduKnowsNgrams for a recent project on [data augmentation](https://github.com/jaaack-wang/linguistic-knowledge-in-DA-for-NLP).
- Download: https://drive.google.com/file/d/1IA7HfpYrB5XRUPSV69DVKl2PANU5NvpH/view?usp=sharing