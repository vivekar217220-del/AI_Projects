# Generative AI Prototypes

Two Python notebook experiments that compare a conversational interface with a focused text summarization tool.

| Prototype | Implementation | Source |
| --- | --- | --- |
| Chatbot | Sends conversation prompts to Groq and displays the responses in a Gradio interface. | [ChatBox](ChatBox) |
| Text summarizer | Runs Hugging Face Transformers with `t5-small` and exposes a text input through Gradio. | [Text_Summarizer](Text_Summarizer) |

## Explore the prototypes

The source files are notebook exports. The chatbot requires a Groq API key supplied in the notebook environment. The summarizer can be explored directly in the [Colab notebook](https://colab.research.google.com/drive/16eq4xWrxKD2qtFc09EMAewZbTVjjxcPj?usp=sharing).
