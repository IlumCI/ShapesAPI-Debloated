## Implementation Examples

### 🐍 Python

```python
from openai import OpenAI

shapes_client = OpenAI(
    api_key="<your-API-key>",
    base_url="https://api.shapes.inc/v1/",
)

response = shapes_client.chat.completions.create(
    model="shapesinc/<shape-username>",
    messages=[
        {"role": "user", "content": "Hello"}
    ]
)

print(response)
```

### 🌐 JavaScript

```javascript
const openai = require("openai");

const shapes_client = new OpenAI({
    apiKey: "<your-API-key>",
    baseURL: "https://api.shapes.inc/v1",
});

const response = await shapes_client.chat.completions.create({
    model: "shapesinc/<shape-username>",
    messages: [
        { role: "user", content: "Hello" }
    ]
});

console.log(response);
```

### 🔄 CURL

```bash
curl -X POST https://api.shapes.inc/v1/chat/completions \
     -H "Authorization: Bearer <your-API-key>" \
     -H "Content-Type: application/json" \
     -d '{"model": "shapesinc/<shape-username>", "messages": [{ "role": "user", "content": "Hello" }]}'
```

### Quick Setup

| Requirement | Details |
|-------------|---------|
| Base URL | `https://api.shapes.inc/v1/` |
| Model Format | `shapesinc/<shape-username>` |
| Authentication | Bearer token in Authorization header |
| Environment Variables | `SHAPESINC_API_KEY` and `SHAPESINC_SHAPE_USERNAME` |

### API Specifications

| Feature | Details |
|---------|---------|
| Endpoints | `/chat/completions` |
| Rate Limits | 5 RPM  |
| Headers | `X-User-Id` for user identification, `X-Channel-Id` for conversation context |
| Response Format | Standard OpenAI-compatible JSON response |

## Supported Commands

Shapes now support the following commands:
- `!reset` - Reset the Shape's long-term memory
- `!sleep` - Generate a long-term on demand 
- `!dashboard` - Access the Shape's dedicated dashboard for configuration
- `!info` - Get information about the shape
- `!web` - Search the web (now free for all users)
- `!help` - Get help with commands
- `!imagine` - Generate images
- `!wack` - Reset the Shape's short-term memory

## Advanced Features

| Feature | Details |
|---------|---------|
| Vision Support | Send OpenAI API compatible image_url with user messages |
| Tool Calling | Shapes now support tool calling and MCP functionality |
| Voice Features | Free voice for all shapes (custom or pre-made voices via shapes.inc) |
| Voice Configuration | Option to disable voice transcripts (set via shapes.inc) |
| Voice Formatting | Improved formatting for voice URLs with new line separation |


## API Multimodal Support

The Shapes API supports multiple types of input modalities:

### Image Support
You can send image URLs in the API request using this format:
```json
{
  "model": "shapesinc/your_shape",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "What's in this image?"
        },
        {
          "type": "image_url",
          "image_url": {
            "url": "https://example.com/image.jpg"
          }
        }
      ]
    }
  ]
}
```

### Audio Support
You can send audio URLs in the API request using this format:
```json
{
  "model": "shapesinc/your_shape",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "Please transcribe and respond to this audio message"
        },
        {
          "type": "audio_url",
          "audio_url": {
            "url": "https://example.com/audio.mp3"
          }
        }
      ]
    }
  ]
}
```

Supported audio formats: mp3, wav, ogg
