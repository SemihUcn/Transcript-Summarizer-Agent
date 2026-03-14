# Transcript Summarizer using Langgraph and Llama3

A scalable transcript summarizer application built with Python, Ollama API, LLaMA3, LangChain, and Gradio. This application can handle long transcriptions that exceed the context window by chunking and processing them efficiently.


### Prerequisites

- Python 3.8+ (tested with Python 3.13)
- Docker & Docker Compose (for containerized deployment)
- Ollama running locally with LLaMA3 model

## Usage

1. **Upload VTT File:** Click on the file upload area and select your .vtt transcript file
2. **Configure Settings:** Adjust chunk size and overlap settings if needed
3. **Generate Summary:** Click "Generate Summary" to process the transcript
4. **Review Results:** View the generated summary and processing statistics

## Configuration

The application can be configured through environment variables or by creating a `.env` file in the project root:

- `OLLAMA_BASE_URL`: Ollama API base URL (default: http://localhost:11434)
- `MODEL_NAME`: LLaMA model name (default: llama3.1:8b)
- `CHUNK_SIZE`: Maximum tokens per chunk (default: 2000)
- `CHUNK_OVERLAP`: Token overlap between chunks (default: 200)
- `GRADIO_PORT`: Gradio server port (default: 7860)
- `MAX_CONCURRENT_REQUESTS`: Maximum concurrent API requests (default: 3)
- `REQUEST_TIMEOUT`: Request timeout in seconds (default: 300)
- `TEMPERATURE`: Temperature for text generation (default: 0.3)
- `LOG_LEVEL`: Logging level - DEBUG, INFO, WARNING, ERROR, or CRITICAL (default: INFO)

### Environment File Setup

Copy the example environment file and modify as needed:
```bash
cp .env.example .env
```

Then edit `.env` with your preferred settings:
```env
# Example .env configuration
OLLAMA_BASE_URL=http://localhost:11434
MODEL_NAME=llama3.1:8b
CHUNK_SIZE=2000
CHUNK_OVERLAP=200
TEMPERATURE=0.3
GRADIO_PORT=7860
MAX_CONCURRENT_REQUESTS=3
REQUEST_TIMEOUT=300
LOG_LEVEL=INFO
```

## Development

### Running Tests
```bash
# Run all tests
python -m pytest tests/

# Test specific modules
python -m pytest tests/test_config.py -v        # Test configuration loading
python -m pytest tests/test_chunker.py -v       # Test text chunking
python -m pytest tests/test_vtt_parser.py -v    # Test VTT parsing
python -m pytest tests/test_ollama_service.py -v # Test Ollama integration
```



