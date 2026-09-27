# LLM Engineering Projects

LLM applications built with Python, Hugging Face and Gradio.

## Synthetic Data Generator

A tool that generates realistic synthetic data from a plain-text request, powered by an open-source LLM running on a GPU.

Type a request like *"Give me 5 customer reviews for a pizza restaurant"* or *"Give me 10 fake customers with name, age and city"*, and the model returns realistic, varied data.

### Why synthetic data?
- **Testing:** fill a new system with data that looks real
- **Privacy:** work with realistic data without exposing real personal information
- **Training:** create examples when real data is scarce

### How it works
1. Loads **Llama 3.2 3B Instruct** (Meta) from Hugging Face
2. Compresses the model to **4-bit** with bitsandbytes, reducing it from ~6.4 GB to ~2.3 GB of GPU memory
3. Wraps the prompt in the model's chat template, generates a response, and decodes only the newly generated tokens
4. Exposes everything through a simple **Gradio** interface

### Why an open-source model?
The model runs entirely on the notebook's own GPU. No data is sent to an external API, and there is no per-request cost.

### Tech stack
Python · Hugging Face Transformers · bitsandbytes · PyTorch · Gradio · Google Colab (T4 GPU)

### Run it yourself
1. Open the notebook with the **Open in Colab** button
2. Select a GPU: *Runtime → Change runtime type → T4 GPU*
3. Request access to [Llama 3.2 3B Instruct](https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct) on Hugging Face
4. Add your Hugging Face token to Colab Secrets as `HF_TOKEN`
5. Run all cells

### Next steps
- Return structured output (tables) that can be downloaded as CSV
- Let the user choose between several open-source models
- Control the number of rows and the fields generated
