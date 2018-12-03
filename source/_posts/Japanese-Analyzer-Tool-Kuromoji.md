title: 跟着日语分词器Kuromoji学习日语
author: Tim Zhang
tags:
  - 日语
  - 分词
  - Java
  - Kuromoji
  - Word Analyzer
categories:
  - 日语
  - Kuromoji
  - Word Analyzer
  - Java
date: 2018-12-03 13:38:00
---

## Kuromoji简介

> Kuromoji is an open source Japanese morphological analyzer written in Java.

> Kuromoji has been donated to the Apache Software Foundation and provides the Japanese language support in Apache Lucene and Apache Solr 3.6 and 4.0 releases, but it can also be used separately.

> Official Site Url(http://www.atilika.org/)



## 下载Jar包

Kuromoji 0.7.7 (https://github.com/atilika/kuromoji/downloads)

## 测试代码如下

```java
import java.util.Arrays;
import java.util.List;
import java.util.logging.Logger;

import org.atilika.kuromoji.Token;
import org.atilika.kuromoji.Tokenizer;
import org.atilika.kuromoji.Tokenizer.Builder;



public class KuromojiUtil {

	private static final Logger logger = Logger.getLogger(KuromojiUtil.class.getName());

	public static void main(String[] args) {
		logger.info("testAnalyzerModeNormal start!");
		testAnalyzerModeNormal();
	}

	/**
	 * 分词模式
	 */
	public static void testAnalyzerModeNormal(){
		String word = "日本経済新聞でモバゲーの記事を読んだ。";
		Builder builder = Tokenizer.builder();

		// Normal
		Tokenizer normal = builder.build();
		List<Token> tokensNormal = normal.tokenize(word);
		disp(tokensNormal);
	}


	public static void disp(List<Token> tokens){
		for (Token token : tokens) {
		    System.out.println("==================================================");
		    System.out.println("allFeatures : " + token.getAllFeatures());
		    System.out.println("partOfSpeech : " + token.getPartOfSpeech());
		    System.out.println("position : " + token.getPosition());
		    System.out.println("reading : " + token.getReading());
		    System.out.println("surfaceFrom : " + token.getSurfaceForm());
		    System.out.println("allFeaturesArray : " + Arrays.asList(token.getAllFeaturesArray()));
		    System.out.println("辞書にある言葉? : " + token.isKnown());
		    System.out.println("未知語? : " + token.isUnknown());
		    System.out.println("ユーザ定義? : " + token.isUser());
		}
	}

}
```

## 测试方法运行结果：

```sh
情報: testAnalyzerModeNormal start!
==================================================
allFeatures : 名詞,固有名詞,組織,*,*,*,日本経済新聞,ニホンケイザイシンブン,ニホンケイザイシンブン
partOfSpeech : 名詞,固有名詞,組織,*
position : 0
reading : ニホンケイザイシンブン
surfaceFrom : 日本経済新聞
allFeaturesArray : [名詞, 固有名詞, 組織, *, *, *, 日本経済新聞, ニホンケイザイシンブン, ニホンケイザイシンブン]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 助詞,格助詞,一般,*,*,*,で,デ,デ
partOfSpeech : 助詞,格助詞,一般,*
position : 6
reading : デ
surfaceFrom : で
allFeaturesArray : [助詞, 格助詞, 一般, *, *, *, で, デ, デ]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 名詞,一般,*,*,*,*,*
partOfSpeech : 名詞,一般,*,*
position : 7
reading : null
surfaceFrom : モバゲー
allFeaturesArray : [名詞, 一般, *, *, *, *, *]
辞書にある言葉? : false
未知語? : true
ユーザ定義? : false
==================================================
allFeatures : 助詞,連体化,*,*,*,*,の,ノ,ノ
partOfSpeech : 助詞,連体化,*,*
position : 11
reading : ノ
surfaceFrom : の
allFeaturesArray : [助詞, 連体化, *, *, *, *, の, ノ, ノ]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 名詞,一般,*,*,*,*,記事,キジ,キジ
partOfSpeech : 名詞,一般,*,*
position : 12
reading : キジ
surfaceFrom : 記事
allFeaturesArray : [名詞, 一般, *, *, *, *, 記事, キジ, キジ]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 助詞,格助詞,一般,*,*,*,を,ヲ,ヲ
partOfSpeech : 助詞,格助詞,一般,*
position : 14
reading : ヲ
surfaceFrom : を
allFeaturesArray : [助詞, 格助詞, 一般, *, *, *, を, ヲ, ヲ]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 動詞,自立,*,*,五段・マ行,連用タ接続,読む,ヨン,ヨン
partOfSpeech : 動詞,自立,*,*
position : 15
reading : ヨン
surfaceFrom : 読ん
allFeaturesArray : [動詞, 自立, *, *, 五段・マ行, 連用タ接続, 読む, ヨン, ヨン]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 助動詞,*,*,*,特殊・タ,基本形,だ,ダ,ダ
partOfSpeech : 助動詞,*,*,*
position : 17
reading : ダ
surfaceFrom : だ
allFeaturesArray : [助動詞, *, *, *, 特殊・タ, 基本形, だ, ダ, ダ]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
==================================================
allFeatures : 記号,句点,*,*,*,*,。,。,。
partOfSpeech : 記号,句点,*,*
position : 18
reading : 。
surfaceFrom : 。
allFeaturesArray : [記号, 句点, *, *, *, *, 。, 。, 。]
辞書にある言葉? : true
未知語? : false
ユーザ定義? : false
```
