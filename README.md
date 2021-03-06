RSA-Algorithm
=============

RSA算法演示程序，仅供了解RSA算法实现原理

## RSA算法原理

- 找出两个"很大"的质数：P & Q
- N = P * Q
- M = (P - 1) * (Q - 1)
- 找出整数E，E与M互质，即除了1之外，没有其他公约数
- 找出整数D，使得E*D除以M余1，即 (E * D) % M = 1

经过上述准备工作之后，可以得到：
* E是公钥，负责加密
* D是私钥，负责解密
* N负责公钥和私钥之间的联系
* 加密算法，假定对X进行加密
  - `(X ^ E) % N = Y`
* 根据费尔马小定义，根据以下公式可以完成解密操作
  - `(Y ^ D) % N = X`

RSA本身算法的核心思想还是比较简单的，加密、解密算法的区别也只是在乘方取模部分使用的数字有所区别而已

当然，实际运用要比示例代码复杂得多，由于RSA算法的公钥私钥的长度（模长度）要到1024位甚至2048位才能保证安全，
因此，P、Q、E的选取，公钥、私钥的生成，加密、解密模指数运算都有一定的计算程序，需要依托计算机高速运算来完成。

## 公开密钥的好处

* `简单` 就是一些乘除而已
* `可靠` 可以保证产生的密文是统计独立，并且分布均匀的，也就是说：
  - 不论给出多少份明文和对应的密文，也无法根据已知的明文和密文的对应关系，破译出下一份密文
  - N和E可以公开给任何人加密使用，但是只有掌握密钥D的人才可以解密，即使加密者自己也无法解密
* `灵活` 可以产生很多的公钥E和私钥D的组合给不同的加密者

## 测试数据说明

```ruby
P = 11;
Q = 13;
N = 143;
M = 120;

E = 89;
D = 209;
```

提示：本示例程序仅用于演示，N的数值只有143，能够加密的字符范围有限。

## 致谢

本示例程序的思想，参照吴军博士的《数学之美》一书，在此表示感谢！
