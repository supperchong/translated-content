---
title: 加密
slug: Glossary/Encryption
translation_of: Glossary/Encryption
---
在密码学（{{glossary("cryptography")}}）领域，**加密**是指把明文（{{glossary("plaintext")}}）转换成密文（{{glossary("ciphertext")}}）的过程。密文应该对非授权用户不可读。

加密是一个密码学原语：它通过一种称作 {{glossary("cipher")}} 的编码技术，把纯文本信息转换为密文。现代密码的加密算法是通过特定的密码算法来工作的，称为{{glossary("key","密钥")}}。由于算法常常是公开的，若要保证加密安全，就必须确保密钥高度保密。

![How encryption works.](encryption.png)

如果不知道密钥，其逆过程{{glossary("decryption","解密")}}在数学上是很难做到的。究竟有多难做到，取决于算法的安全性，以及{{glossary("cryptanalysis","密码分析学")}}的发展程度。
