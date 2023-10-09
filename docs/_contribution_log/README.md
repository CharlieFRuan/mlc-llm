# Contribution Log

The goal of this page is to record your contribution for new models
compiled with MLC-LLM.

While you could directly submit a PR to modify the documentation--this page simply
provides a more lightweight and buffer-like method.

We will sync the contributions here to the official documentation's [prebuilt model page](https://llm.mlc.ai/docs/prebuilt_models.html) once in a while.

## How to add an entry
1. ✏️ Click on the pencil icon in the top right corner to edit this file
    1. Add the model you are contributing. Make sure to include:
        - Model variant (e.g. `CodeLlama`)
        - The parameter size (e.g. `34b`)
        - Type if applicable (e.g. `Instruct`, `Chat`, etc.)
        - Quantization scheme (e.g. `q4f16`)
    3. Add the hugging face link where you uploaded your compiled model.
    4. Add the original model link (preferably hugging face).
    5. Add your github handle if you'd like!
2. Click `Commit changes...`
3. Click `Create a new branch for this commit and start a pull request`.
4. After confirming your changes, click `Create a pull request`.
5. 🎉 Then your PR is live! We will merge in the PR, and sync to the documentation once in a while.

|  Model   | Compiled Model HF Link |  Original Model Link  | Contributor (optional)  | Sync'd to documentation? |
| -------- |:----------------------:|:---------------------:| :----------------------:| :-----------------------:|
| CodeLlama-34b-Instruct-hf-q0f16 | [compiled-hf-link](https://huggingface.co/mlc-ai/mlc-chat-CodeLlama-34b-Instruct-hf-q0f16) | [original-link](https://huggingface.co/codellama/CodeLlama-34b-hf)     | [@mlc-bot](https://github.com/mlc-bot) | ✅ |
| Llama-2-70b-chat-hf-q4f16_1     | [compiled-hf-link](https://huggingface.co/mlc-ai/mlc-chat-Llama-2-70b-chat-hf-q4f16_1)     | [original-link](https://huggingface.co/meta-llama/Llama-2-70b-chat-hf) | [@mlc-bot](https://github.com/mlc-bot) | ✅ |
