# AITuber-Projects: youtube_chat_llm_tts

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

This project enables you to create an AI VTuber that can interact with viewers in real-time through YouTube Live chat. It leverages a fine-tuned Large Language Model (LLM) for generating responses and VOICEVOX for text-to-speech.

## Overview

The `youtube_chat_llm_tts.ipynb` notebook contains the code for an AI VTuber that performs the following actions:

1. Retrieves live chat messages from a specified YouTube Live stream using the YouTube Data API.
2. Analyzes the sentiment of each chat message using a sentiment analysis model (currently using `cardiffnlp/twitter-roberta-base-sentiment-latest`).
3. Generates a response using a fine-tuned LLM based on the chat message and its sentiment.
    -   The current implementation uses a fine-tuned [Llama-3.1-Swallow-8B-Instruct-v0.1](https://huggingface.co/tokyotech-llm/Llama-3.1-Swallow-8B-Instruct-v0.1) and my custom qLora model.
4. Converts the generated response to speech using VOICEVOX.
    -   Future updates may include the use of a custom fine-tuned voice model.
5. Plays the generated audio as the VTuber's voice.

## Requirements

-   Google Colab Pro (or a similar environment with GPU support)
-   A 3D model in VRM format.
-   VMagicMirror (or a similar software for controlling the 3D model).
-   OBS Studio for streaming.
-   YouTube Data API key.
-   YouTube Channel ID.
-   Hugging Face account and access token.
-   VOICEVOX (or a similar TTS engine).
-   The following Python libraries (listed in the notebook's installation section):
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

## Setup

1. **Install necessary libraries:** Run the installation cells in the notebook to install all required Python packages and download necessary resources like the VOICEVOX core and ONNX Runtime.
2. **Set up API keys and IDs:**
    -   Obtain a YouTube Data API key from the Google Cloud Console.
    -   Get your YouTube Channel ID.
    -   Retrieve your Hugging Face access token.
    -   Store these credentials securely using Google Colab's secrets manager.
3. **Configure the 3D model and streaming software:**
    -   Create your 3D model using VRoid Studio and export it in VRM format.
    -   Set up VMagicMirror (or a similar software) to control your 3D model's movements and expressions.
    -   Configure OBS Studio to capture the VMagicMirror window and your audio output.
4. **Modify the `video_id` in the `main()` function:** Replace `"ここにYoutube LIVE IDを入力"` with the actual ID of your YouTube Live stream.
5. **Run the notebook:** Execute the cells in the `youtube_chat_llm_tts.ipynb` notebook to start the AI VTuber.

## Usage

1. Start your YouTube Live stream.
2. Run the `youtube_chat_llm_tts.ipynb` notebook.
3. The AI VTuber will start responding to live chat messages in real-time.

## Future Enhancements

-   **Custom Voice Model:** The current implementation uses VOICEVOX for text-to-speech. Future updates aim to incorporate a custom fine-tuned voice model to give the AI VTuber a more unique voice.
-   **Improved LLM:** Further fine-tuning and optimization of the LLM to generate more engaging and contextually relevant responses.
-   **More Robust Error Handling:** Implement more comprehensive error handling and recovery mechanisms.

## License

This code is provided under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/) with the following additional clause:

-   **Selling this code (or modified versions of it) is not permitted.**

This means that:

-   **Attribution (BY):** You must give appropriate credit to the original author when distributing modified versions of the code.
-   **ShareAlike (SA):** If you modify this code and distribute it, you must apply the same license as the original (including the prohibition of selling the code).

## Disclaimer

This project is for educational and demonstration purposes only. The author is not responsible for any damages or liabilities arising from the use of this code. Use at your own risk.

The author is not affiliated with any of the services or models used in this project (YouTube, Hugging Face, VOICEVOX, etc.).

This project uses third-party models and libraries, each with its own license. Please refer to the respective licenses for each component.

The generated responses are based on a machine learning model and may not always be accurate, appropriate, or safe. User discretion is advised.
