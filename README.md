# LLM Text Generation Playground

An interactive Jupyter notebook playground for experimenting with different language models and text generation strategies.

## Features

- **Multiple Models**: Switch between GPT-2 and Qwen3-0.6B
- **Decoding Strategies**: Compare greedy, top-k, and top-p sampling
- **Temperature Control**: Adjust generation randomness from 0.1 to 2.0
- **Interactive UI**: User-friendly interface with real-time feedback
- **Loading Indicators**: Visual feedback during text generation

## Requirements

```bash
pip install transformers torch ipywidgets
```

### Hardware
- **GPU**: CUDA-compatible GPU (recommended)
- **MPS**: Apple Silicon support
- **CPU**: Falls back to CPU if no GPU available

## Usage

1. **Run the notebook** to load models (first run may take a few minutes to download)
2. **Enter your prompt** in the text area
3. **Select model**: Choose between GPT-2 or Qwen3-0.6B
4. **Choose strategy**:
   - **Greedy**: Deterministic, always picks highest probability token
   - **Top-k**: Samples from top 50 most likely tokens
   - **Top-p**: Nucleus sampling (samples from smallest set with cumulative probability ≥ 0.9)
5. **Adjust temperature**: Higher = more random, lower = more focused
6. **Click Generate**: Watch the loading indicator while text is generated

## Models

### GPT-2
- **Size**: 124M parameters
- **Best for**: General English text generation
- **Speed**: Fast

### Qwen3-0.6B
- **Size**: 600M parameters  
- **Best for**: More coherent longer-form text
- **Speed**: Moderate

## Decoding Strategies

| Strategy | Temperature | Best Use Case |
|----------|-------------|---------------|
| Greedy | N/A | Factual, deterministic output |
| Top-k | 0.7-1.0 | Balanced creativity and coherence |
| Top-p | 0.8-1.2 | Creative writing, varied outputs |

## Tips

- Start with **greedy** decoding to see the model's most confident prediction
- Use **temperature 0.7-1.0** for balanced results
- Try **temperature > 1.0** for more creative/random outputs
- Use **temperature < 0.7** for more focused/conservative outputs

## Limitations

- Max output length: 100 tokens
- Models load on first run (requires internet connection)
- Generation speed depends on hardware
- Button may show hover effects when disabled (visual only, clicks are blocked)

## License

This project uses models from Hugging Face:
- GPT-2: [OpenAI](https://huggingface.co/gpt2)
- Qwen3-0.6B: [Qwen](https://huggingface.co/Qwen/Qwen3-0.6B)

## Troubleshooting

**Models not loading?**
- Ensure you have internet connection
- Check that transformers and torch are installed
- Verify sufficient disk space for model downloads

**Slow generation?**
- Check if CUDA/MPS is available
- Try the smaller GPT-2 model
- Reduce max_new_tokens in the code

**Out of memory?**
- Use GPT-2 instead of Qwen
- Restart kernel and try again
- Close other applications using GPU memory