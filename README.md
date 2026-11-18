# Generative AI Projects

Two Python notebook prototypes for exploring different text workflows. The chatbot supports a conversation through a hosted model, while the summarizer takes a document excerpt and generates one shorter result with a pretrained T5 model.

## Project guide

| Prototype | Input | Implementation | Source |
| --- | --- | --- | --- |
| Groq chatbot | A message and conversation history | Hosted model via the Groq API, with a Gradio chat interface | [ChatBox](ChatBox) |
| T5 text summarizer | An article, note, or other text excerpt | Hugging Face Transformers, a pretrained `t5-small` model, and a Gradio text form | [Text_Summarizer](Text_Summarizer) |

## Chatbot workflow

```text
User message -> Gradio chat -> Conversation handler -> Groq API -> Response in chat
```

The chat interface stores the messages in the current conversation and passes the history through its submit handler so the model can respond to follow-ups. The snapshot reads the Groq credential from Colab's Secrets panel. Use your own credential when reproducing the notebook flow and keep it in the notebook's secret store.

To review the ordinary chat flow, follow the Gradio textbox's submit handler and the conversation request in the [ChatBox snapshot](ChatBox). With a configured notebook session, test a general question followed by a clarification and check how the second answer uses the earlier message.

## Summarizer workflow

```text
Text excerpt -> T5 tokenizer -> Beam-search generation -> Decoded summary -> Gradio output
```

The source loads a pretrained `t5-small` tokenizer and model, prefixes the text with `summarize: `, and encodes it with truncation. It generates a summary with four beams and decodes the output back into text. This experiment uses the pretrained model directly.

1. Open the [summarizer notebook in Google Colab](https://colab.research.google.com/drive/16eq4xWrxKD2qtFc09EMAewZbTVjjxcPj?usp=sharing).
2. Follow the notebook cells for dependencies, model loading, summarization, and Gradio setup.
3. Try a short passage that contains several specific facts. Compare the result with the original for omissions or changes in meaning.

The [standalone companion repository](https://github.com/vivekar217220-del/genai-text-summarizer) includes the notebook link, an interface preview, and a detailed walkthrough of the same summarizer.

## Repository and evaluation notes

The files are notebook-oriented snapshots. Use them to inspect the implementation or reconstruct the experiments in separate notebook cells. Chat requires a working Groq connection. The summarizer truncates long input at its token limit, and both prototypes can omit or misstate details. Check output against the supplied text when evaluating it.
