# AITuber-Projects: youtube_chat_llm_tts

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

このプロジェクトでは、YouTube Liveチャットを通じて視聴者とリアルタイムで対話できるAI VTuberを作成することができます。応答生成にはファインチューニングされた大規模言語モデル（LLM）、音声合成にはVOICEVOXを活用しています。

## 概要

`youtube_chat_llm_tts.ipynb` ノートブックには、以下の動作を行うAI VTuberのコードが含まれています。

1. YouTube Data APIを使用して、指定されたYouTube Live配信からライブチャットメッセージを取得します。
2. 感情分析モデル（現在は `cardiffnlp/twitter-roberta-base-sentiment-latest` を使用）を用いて、各チャットメッセージの感情を分析します。
3. チャットメッセージとその感情に基づいて、ファインチューニングされたLLMを使用して応答を生成します。
    -   現在の実装では、ファインチューニングされた [Llama-3.1-Swallow-8B-Instruct-v0.1](https://huggingface.co/tokyotech-llm/Llama-3.1-Swallow-8B-Instruct-v0.1) と、このモデルをベースに私が作成したカスタムqLoraモデルを使用しています。
4. 生成された応答をVOICEVOXを使用して音声に変換します。
    -   将来のアップデートでは、カスタムのファインチューニングされた音声モデルの使用が含まれる可能性があります。
5. 生成された音声をVTuberの声として再生します。

## 動作環境

-   Google Colab Pro（またはGPUをサポートする同様の環境）
-   VRM形式の3Dモデル
-   VMagicMirror（または3Dモデルを制御するための同様のソフトウェア）
-   配信用OBS Studio
-   YouTube Data APIキー
-   YouTubeチャンネルID
-   Hugging Faceアカウントとアクセストークン
-   VOICEVOX（または同様のTTSエンジン）
-   以下のPythonライブラリ（ノートブックのインストールセクションに記載）：
    -   `google-api-python-client`
    -   `requests`
    -   `transformers`
    -   `torch`
    -   `sounddevice`
    -   `scipy`
    -   `soundfile`
    -   `pydub`
    -   `fugashi`
    -   `ipadic`
    -   `accelerate`
    -   `bitsandbytes`
    -   `peft`
    -   `huggingface_hub`

## セットアップ

1. **必要なライブラリのインストール:** ノートブックのインストールセルを実行して、必要なすべてのPythonパッケージをインストールし、VOICEVOXコアやONNX Runtimeなどの必要なリソースをダウンロードします。
2. **APIキーとIDの設定:**
    -   Google Cloud ConsoleからYouTube Data APIキーを取得します。
    -   YouTubeチャンネルIDを取得します。
    -   Hugging Faceのアクセストークンを取得します。
    -   これらの認証情報をGoogle Colabのシークレットマネージャーを使用して安全に保存します。
3. **3Dモデルと配信ソフトウェアの設定:**
    -   VRoid Studioを使用して3Dモデルを作成し、VRM形式でエクスポートします。
    -   VMagicMirror（または同様のソフトウェア）をセットアップして、3Dモデルの動きや表情を制御します。
    -   OBS Studioを設定して、VMagicMirrorウィンドウと音声出力をキャプチャします。
4. **`main()` 関数内の `video_id` の変更:** `"ここにYoutube LIVE IDを入力"` を実際のYouTube Live配信のIDに置き換えます。
5. **ノートブックの実行:** `youtube_chat_llm_tts.ipynb` ノートブックのセルを実行して、AI VTuberを起動します。

## 使い方

1. YouTube Live配信を開始します。
2. `youtube_chat_llm_tts.ipynb` ノートブックを実行します。
3. AI VTuberがリアルタイムでライブチャットメッセージに応答を開始します。

## 今後の機能拡張

-   **カスタム音声モデル:** 現在の実装では、音声合成にVOICEVOXを使用しています。将来的には、カスタムのファインチューニングされた音声モデルを組み込んで、AI VTuberによりユニークな声を与えることを目指しています。
-   **LLMの改善:** より魅力的で文脈に適した応答を生成するために、LLMのさらなるファインチューニングと最適化を行います。
-   **より堅牢なエラー処理:** より包括的なエラー処理と回復メカニズムを実装します。

## ライセンス

このコードは、[Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/deed.ja)の下で提供されており、以下の追加条項が適用されます。

-   **このコード（またはその改変版）の販売は許可されていません。**

これは以下のことを意味します。

-   **表示（BY）:** コードの改変版を配布する際には、元の作者を適切にクレジット表示する必要があります。
-   **継承（SA）:** このコードを改変して配布する場合は、元のライセンス（コードの販売禁止を含む）と同じライセンスを適用する必要があります。

## 免責事項

このプロジェクトは教育およびデモンストレーションのみを目的としています。作者は、このコードの使用に起因するいかなる損害または責任についても責任を負いません。自己責任で使用してください。

作者は、このプロジェクトで使用されているいかなるサービスやモデル（YouTube、Hugging Face、VOICEVOXなど）とも提携していません。

このプロジェクトはサードパーティのモデルとライブラリを使用しており、それぞれに独自のライセンスがあります。各コンポーネントのそれぞれのライセンスを参照してください。

生成される応答は機械学習モデルに基づいており、常に正確、適切、または安全であるとは限りません。ユーザーの裁量で使用してください。
