---
layout: post
title: マイク入力のノイズ除去
date: 2020-05-25 17:26:00 +0900
---

PCにマイクを繋げて通話する機会も増えて，ゲインをかけたりノイズ除去したりしたくなってきた．
OBSでフィルタをかければノイズ除去-->ゲイン-->コンプレッサ-->ノイズゲートをかけて聞き取りやすくできることが分かったが，これを通話にも使いたかった．

結論として，audio output を audio input に転送する virtual audio cable を使えば良いらしい．[reddit の post](https://www.reddit.com/r/obs/comments/aoinga/use_obs_audio_output_as_a_microphone_source/)が参考になった．[VB-CABLE](https://www.vb-audio.com/Cable/)をインストールして，OBSのマイク入力をモニタし，モニタした内容をOBSの設定-->音声-->詳細設定の「モニタリングデバイスで「CABLE Input (VB-Audio Virtual Cable)」を選択して，通話アプリのOutput をマイク入力として選択すれば，OBSのフィルタがかかった音声を通話アプリのマイク入力に転送できた．

