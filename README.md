# 🎬 ClipIt - Semantic Media Clipper

ClipIt is an AI-powered Openclaw Skill powered by Elevenlabs APIs that allows you to find, cut, and process audio or video segments using natural language. Instead of manually searching through timelines, you can simply describe the part you want to extract.

## 🌟 Key Features
*   **Semantic Clipping**: Find segments using natural language queries (e.g., *"Find the part where they talk about the budget"*).
*   **Automatic Transcription**: Powered by **ElevenLabs Scribe** with word-level precision.
*   **AI Intelligence**: Uses **OpenAI GPT-4o-mini** to intelligently identify start/end points and maintain sentence integrity.
*   **Audio Isolation**: Remove background noise and clean up vocals using ElevenLabs Audio Isolation.
*   **Instant Dubbing**: Translate your clips into 29+ languages while maintaining the original voice timing.
*   **YouTube Support**: Process videos directly from YouTube URLs.

## 🛠 Prerequisites
*   Python 3.8+
*   FFmpeg (installed on your system and in PATH)
*   [ElevenLabs API Key](https://elevenlabs.io/)
*   [OpenAI API Key](https://platform.openai.com/)

## 🚀 Installation

1.  **Clone the repository**:
    ```bash
    git clone <repository-url>
    cd clip
    ```

2.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Set up environment variables**:
    ```bash
    export ELEVENLABS_API_KEY="your_key_here"
    export OPENAI_API_KEY="your_key_here"
    ```

## 📖 Usage

ClipIt comes with a convenient wrapper script called `clipper`.

### Basic Clipping
```bash
./bin/clipper --input "meeting.mp4" --query "discussion about the deadline"
```

### YouTube Clipping + Isolation
```bash
./bin/clipper --input "https://youtu.be/..." --query "the intro joke" --isolate
```

### Clipping + Dubbing to Hindi
```bash
./bin/clipper --input "tutorial.mp3" --query "how to install" --dub "hi"
```

### Advanced Flags
| Flag | Description |
| :--- | :--- |
| `--input`, `-i` | (Required) Path to local file or YouTube URL |
| `--query`, `-q` | (Required) Natural language description of the segment |
| `--output`, `-o` | Custom output filename |
| `--context`, `-c` | Padding in seconds to add to the start/end (e.g., `0.5`) |
| `--isolate` | Flag to remove background noise |
| `--dub` | Language code for translation (e.g., `es`, `fr`, `ja`) |

## 🔄 How it Works
1.  **Transcribe**: Extracts audio and gets word-level timestamps from ElevenLabs.
2.  **Analyze**: OpenAI identifies the best logical segment based on your query.
3.  **Refine**: Backtracks to sentence boundaries to ensure no "half-words" are caught.
4.  **Cut**: Uses FFmpeg to precisely trim the media.
5.  **Post-Process**: Optionally isolates or dubs the resulting clip.

---
Built with ❤️ using ElevenLabs and OpenAI.
