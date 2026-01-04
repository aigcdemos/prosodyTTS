# Title：Prosody Injection for LLM-based TTS System

[![Paper](https://img.shields.io/badge/Paper-PDF-red)](link-to-paper.pdf)
[![Conference](https://img.shields.io/badge/Conference-ConferenceName-Year-blue)](conference-link)
[![GitHub stars](https://img.shields.io/github/stars/yourusername/repo?style=social)](https://github.com/yourusername/repo)

## 📖 Abstract

This paper proposes a prosody modeling and injection method for LLM-based Text-to-Speech (TTS) systems. 
The approach incorporates prosodic markers at specific textual positions to enable precise prosody control. 
Notably, it requires no structural modifications to the base TTS model. 
Instead, prosodic information is extracted from the dataset, and the LLM within the TTS system 
is fine-tuned using text-audio pairs enriched with these prosodic markers. 
This process equips the model with the capability to recognize and reproduce prosodic patterns. 
Concurrently, we fine-tune a text-based LLM to convert user-described emotional cues into sequences of prosodic markers and prompts, 
which are then inserted into the input text. Experiments conducted on the VoxBox Chinese dataset 
demonstrate that our method effectively injects prosodic variations into synthesized speech. 
Demo samples are available at [https://github.com/aigcdemos/prosodyTTS]. 

## 🔍 Contributions

- **1**：A finer-grained prosody extraction method, namely character-level prosody modeling, which enables precise control over the temporal variation of prosody rather than overall prosody control. Specifically, it analyzes the prosodic variation for each character in a sentence and inserts corresponding prosodic markers at positions where prosodic changes are prominent, e.g., if the fundamental frequency (F0) difference between two adjacent characters exceeds a threshold, a rising marker (for increased F0) or a falling marker (for decreased F0) is added. Based on this method, a dataset with detailed descriptions of prosodic changes was built.
- **2**：An LLM fine-tuning method that enables the model to insert fine-grained prosodic control information into the text to be synthesized based on user prompts (e.g., fine-grained emotional changes over time rather than a single overall emotion label), thereby reflecting the temporal variation of prosody.


## 💡 Samples

| 韵律标记&nbsp;&nbsp;&nbsp;&nbsp; | TTS文本 | 标记前&nbsp;&nbsp;&nbsp;&nbsp; | 标记后&nbsp;&nbsp;&nbsp;&nbsp; |
|:--------:|:--------|:------:|:------:|
| **长音** | 拖音的拖→字应该持续很长时间。 | [长音前](samples/贾宝玉_drawl_ori_0.wav) | [长音后](samples/贾宝玉_drawl_flow_llm_label_0.wav)|
| **长音** | 直播间的家人们，我→们直播间带来→了苹果最新的十→七promax，给您带来全新的使用体验。 | [长音前](samples/贾宝玉_long_drawl_ori_1.wav) | [长音后](samples/贾宝玉_long_drawl_flow_llm_label_1.wav) |
| **重音** | 这句话应该是用↑重音进行强调。 | [重音前](samples/贾宝玉_accent_ori_2.wav) | [重音后](samples/贾宝玉_accent_flow_llm_label_2.wav) |
| **升调** | 这句话应该是用↗升调的语气说的。 | [升调前](TTS/samples/贾宝玉_asc_ori_1.wav) | [升调后](samples/贾宝玉_asc_flow_llm_label_1.wav) |
| **降调** | 这句话应该是用↘降调的语气说的。 | [降调前](TTS/samples/贾宝玉_des_ori_0.wav) | [降调后](samples/贾宝玉_des_flow_llm_label_0.wav) |