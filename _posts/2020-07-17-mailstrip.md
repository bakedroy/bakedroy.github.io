---
layout: post
title: 署名から下を消さないで
date: 2020-07-17 12:00:00 +0900
---

Thunderbirdでメールに返信すると，相手からの署名を意味する`-- `から下の行を消してしまう．
相手が自分の返信-->署名-->引用の形式で返信すると，こちらが返信する際に，引用部分がカットされる．
これを回避するには，Thunderbirdの設定エディタから`mail.strip_sig_on_reply`を`false`に設定する必要がある．
結構大事な設定だと思うが，なぜか設定エディタからしか操作できない．
