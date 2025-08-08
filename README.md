# MCP Tools Integration

This project showcases a multi-service AI assistant built with the Model Context Protocol (MCP), integrating the Replicate API, custom API-powered tools, and additional services to deliver end-to-end research and content generation workflows. It combines text-to-speech, web search, AI model execution, and image generation into a single cohesive system. With four integrated services (Replicate, ElevenLabs, SerpAPI, and Tavily) the assistant can quickly gather information, perform deep research, summarize findings, generate high-quality audio narrations, and produce compelling visuals. In short, it’s a versatile, MCP-driven AI assistant designed for speed, accuracy, and multi-modal content creation.

##  Quick Setup

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Configure API Keys
Copy `env_template.txt` to `.env` and add your API keys:
```bash
cp env_template.txt .env
# Edit .env with your actual API keys
```

### 3. Configure MCP in Cursor
Add this to your `~/.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "replicate": {
      "command": "npx",
      "args": ["-y", "replicate-mcp"],
      "env": {
        "REPLICATE_API_TOKEN": "your_token_here"
      }
    },
    "focused-tools": {
      "command": "python",
      "args": ["/path/to/your/project/mcp_server_focused.py"],
      "env": {}
    }
  }
}
```

### 4. Test Setup
```bash
python test_custom_tools.py
```

## Available Tools

### Replicate MCP (35 tools)
- Image generation, training, predictions management
- Direct integration with Replicate's official MCP server

### Focused Tools MCP (5 tools)
- `generate_voice`: ElevenLabs text-to-speech
- `search_web`: SerpAPI web search  
- `search_tavily`: Advanced Tavily search
- `summarize_webpage`: Webpage summarization
- `generate_image`: Replicate image generation

## Architecture

The project uses a dual MCP server setup:
1. **Official Replicate Server**: Full Replicate API access
2. **Custom Focused Server**: Essential tools from multiple APIs

API keys are loaded from `.env` files, making it easy for reviewers to configure their own credentials.

## License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.

## Author

**Prabhu Kiran Avula**

---

*Built with ❤️ using MCP (Model Context Protocol) and various AI APIs*
