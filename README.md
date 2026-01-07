# AI Therapist Chatbot
The AI Therapist chatbot was made to support the mental health of students ages 12 years older. The AI therapist is solutions-focused and will help students find ways to cope with their circumstances to feel better, in a conversational, friendly manner. The chatbot won't help people with suicidal ideation.

## Approach
The transformer model (Blenderbot) was fine-tuned on 3000 dataset rows with equally balanced mental health topics that students face. The transformer model, called Blenderbot, is from Meta and can be found on HuggingFace. It's a text-to-text transformer with 400M parameters, performs well in open-domain conversations, and can display empathy. The max tokens (e.g. context window) are 128 tokens. The output is a text-based response.

To ensure a seamless and context-aware dialogue between the user and chatbot, the system includes the past conversation history within the same client session using Retrieval-Augmented Generation (RAG). The client initiates the interaction by submitting an issue. Then, the relevant past interactions are retrieved from the vector store (FAISS) using RAG. Finally, I applied summarization via bart-large-cnn LLM to the relevant context with a max length of 60 tokens. Additionally, I truncated the context if the overall input message exceeded 126 tokens. 

The chatbot user interface is based on Streamlit, where people can share how they're feeling and receive support from the chatbot.

## Evaluation
The AI therapist's output message was labeled with the counseling skills used (via ChatGPT) and the emotions expressed (via Hume.ai). For evaluation, I compared the counseling skills used by the AI therapist chatbot against the dataset therapist. I also compared the emotions expressed by the AI therapist chatbot and the dataset therapist. I generated the emotion expression via Hume.ai. I calculated the Cosine Similarity to find how similar the AI Therapist was from the dataset therapist. The threshold of 50% or higher similarity was how much overlap I wanted to see between the AI Therapist and the therapist from the dataset. 62.5% of the conversations had a Cosine Similarity of 50% or higher for the counseling skills. 67.5% of the conversations had a Cosine Similarity of 50% of higher the emotions expressed.
