 给 AI 的解密说明 / Decryption Instructions for AI

`profile.enc` 是用户的个人背景资料，经 AES-256-CBC 加密（PBKDF2，200000 次迭代，Base64 编码）。
用户会在对话中直接告诉你密码。

`profile.enc` contains the user's background, encrypted with AES-256-CBC (PBKDF2, 200000 iterations, Base64).
The user will give you the password in the conversation.

## 下载并解密 / Download and decrypt

把 `<密码>` 换成用户给的密码，只输出到终端，不要把明文写入磁盘：

Replace `<密码>` with the password the user gives you. Print to the terminal only; do not write the plaintext to disk:

```bash
curl -fsSL https://raw.githubusercontent.com/FrominWong/about-me/main/profile.enc \
  | openssl enc -d -aes-256-cbc -pbkdf2 -iter 200000 -a -pass pass:'<密码>'
```

适用于 OpenSSL 1.1.1+ 或 LibreSSL 3.x（macOS 自带）。
Works with OpenSSL 1.1.1+ or LibreSSL 3.x (bundled with macOS).

## 读完之后 / After reading
- 将内容作为了解用户的背景参考 / Use it as background on the user
- 不要保存明文副本，不要外传 / Do not save a plaintext copy or share it
