### 机器眼中的单词//How to say a word to machine
#### 众所周知，人类的语言表达是一种很神奇的能力，可以通过各种不同的发音在人与人之间传递信息，
#### 而电脑的世界里，只有数字，处理各种复杂的数据都是转换成2进制的数字，传递给CPU，经过计算后返回一个2进制的结果，再转换成人类可视化的数据。
#### 所以我们人类的语言，也可以转换成数字，让电脑去记住这些数字，并且接收到这些数字时，给我们反馈一个数字。

例如 我们对电脑说一句 I love you
<br />我们可以将其中的各个单词拆开，并且用数字去代表它们。
<br />I love you 中一共有三个单词，分别是 I ， love ， you，我们分别用 1 ，2 ，3 来代表。
<br />以上这个过程我们称之为Tokenize
<br />排序的表示我们用word_index来实现

也就是说如果你有一本书，书中的所有单词都有一个数字来表示，那么这本书中的句子连起来就是一连串的数字。

#### 接下来，就让我们在Python中实现上述的过程。



```python
from tensorflow.keras.preprocessing.text import Tokenizer

sentences = [
    'i love my dog',
    'I, love my cat',
    'You love my dog!'
]

tokenizer = Tokenizer(num_words = 100)  
#初始化对象，num_words =100 最多给多少个单词赋值，就算你拿来一本书，里面有1万个单词，也只给100个词赋值

tokenizer.fit_on_texts(sentences)
#调用tokenizer，给 sentence中的所有单词赋值， 把所有的单词都用数字表示

word_index = tokenizer.word_index
#获取已经被赋值过的单词

print(word_index)
#打印结果

#返回以下结果，1代表love，2代表my，3代表dog。。
#=>{'love': 1, 'my': 2, 'i': 3, 'dog': 4, 'cat': 5, 'you': 6}
```

## 既然把这些单词都赋于了数字的值，那么机器应该能懂了吧，
### 是的，但是先还都是个别的单词，如果要想表达一句话的意思，我们还需要进一步的研究，去发现更多的可循的规律。
#### 请见下回分解

