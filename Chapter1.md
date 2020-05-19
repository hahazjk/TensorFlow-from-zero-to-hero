### 怎样和机器交流//How to say words to machines
#### 众所周知，人类的语言表达是一种很神奇的能力，可以通过各种不同的发音在人与人之间传递信息，
#### 而电脑的世界里，只有数字，处理各种复杂的数据都是转换成2进制的数字，传递给CPU，经过计算后返回一个2进制的结果，再转换成人类可视化的数据。
#### 所以我们人类的语言，也可以转换成数字，让电脑去记住这些数字，并且接收到这些数字时，给我们反馈一个数字。

>例如 我们对电脑说一句 I love you
<br />我们可以将其中的各个单词拆开，并且用数字去代表它们。
<br />I love you 中一共有三个单词，分别是 I ， love ， you，我们分别用 1 ，2 ，3 来代表。这个过程我们称之为Tokenize，*代码中的Step1*
<br />那么 I love you 这句话用数字来表达的话就是 1 2 3，反过来，You love I，这句话就是 3 2 1，
<br />按照顺序将我们已经Tokenize的数字排列起来，对电脑来说就是它所看到的人类语言。排序的表示我们用word_index来实现*代码中的Step2*

也就是说如果你有一本书，书中的所有单词都有一个数字来表示，那么这本书中的句子连起来就是一连串的数字。



```python
from tensorflow.keras.preprocessing.text import Tokenizer

sentences = [
    'i love my dog',
    'I, love my cat',
    'You love my dog!'
]

tokenizer = Tokenizer(num_words = 100)  
#Step1，先初始化对象，num_words =100 最多给多少个单词赋值，就算你拿来一本书，里面有1万个单词，也只给100个词赋值

tokenizer.fit_on_texts(sentences)
#Step1，调用tokenizer，给 sentence中的所有单词赋值， 把所有的单词都用数字表示

word_index = tokenizer.word_index
print(word_index)
```
