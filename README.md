# YouTube Gemini Summarizer

A browser userscript that adds a **"Summarize"** button directly to YouTube video pages.

When clicked, the script opens Gemini, sends the current YouTube video URL, and asks Gemini to generate a detailed summary.

Designed to work with popular userscript managers such as **Tampermonkey** and **Violentmonkey**.

## ✨ Features

* 📺 Adds a **"Summarize"** button to YouTube video pages
* 🤖 Uses **Google Gemini** to generate the summary
* 🔗 Automatically detects the current YouTube video
* 🚀 Opens Gemini automatically and sends the prompt
* ⌨️ Supports `Ctrl + Shift + Click` on YouTube video links
* 🔄 Works with YouTube's single-page navigation
* 🧩 Compatible with Tampermonkey and Violentmonkey
* 🪶 Lightweight — no external dependencies

## 📦 Installation

### 1. Install a userscript manager

You need a browser extension capable of running userscripts.

Recommended options:

* [Tampermonkey](https://www.tampermonkey.net/)
* [Violentmonkey](https://violentmonkey.github.io/)

### 2. Install the script

Open the `.user.js` file from this repository and install it through your userscript manager.

Once installed, open any YouTube video.

You should see a **"Summarize"** button alongside YouTube's video action buttons.

## 🚀 Usage

### Summarize the current video

1. Open a YouTube video.
2. Click **Summarize**.
3. Gemini opens automatically.
4. The video URL is inserted into the prompt.
5. Gemini sends the request and generates the summary.

The default prompt is:

> Hazme un resumen detallado de este video:

followed by the YouTube video URL.

### Keyboard shortcut

You can also use:

**Ctrl + Shift + Click**

on a YouTube video thumbnail or title.

Instead of opening the video normally, the script sends the video URL to Gemini for summarization.

## ⚙️ Configuration

The main prompt can be customized by changing:

```javascript
const PROMPT_BASE = "Hazme un resumen detallado de este video: ";
```

For example:

```javascript
const PROMPT_BASE = "Resume este video en español. Incluye los puntos clave, conceptos importantes y una conclusión: ";
```

You can customize the prompt to make Gemini produce:

* Short summaries
* Detailed summaries
* Bullet-point summaries
* Study notes
* Key takeaways
* Chapter breakdowns
* Technical explanations
* Summaries in a specific language

## 🛠️ How it works

The userscript has two main parts.

### YouTube

The script detects when you are watching a YouTube video and injects the **Summarize** button into the video action bar.

When the button is clicked, it:

1. Extracts the current video's ID.
2. Builds a clean YouTube URL.
3. Stores the prompt using the userscript manager's storage API.
4. Opens Gemini in a new tab.

### Gemini

When Gemini loads, the script checks whether there is a pending summarization request.

If one exists, it:

1. Retrieves the stored prompt.
2. Finds Gemini's text editor.
3. Inserts the prompt.
4. Finds the send button.
5. Automatically sends the request.

## 🔐 Privacy

This script does not use an external server or backend.

The YouTube URL and prompt are passed directly between the userscript and Gemini.

The script does not collect analytics or send data to a third-party server.

You should still review the permissions requested by your userscript manager before installing any userscript.

## ⚠️ Limitations

This project relies on the current HTML structure of YouTube and Gemini.

Both websites can change their interfaces without notice, which may cause:

* The **Summarize** button to stop appearing.
* The Gemini input field to no longer be detected.
* Automatic submission to stop working.

If this happens, the selectors used by the userscript may need to be updated.

## 🗺️ Roadmap

Possible future improvements:

* [ ] Improve Gemini UI compatibility
* [ ] Add customizable prompts
* [ ] Add a settings panel
* [ ] Add multiple summary styles
* [ ] Add support for other AI providers
* [ ] Add automatic language detection
* [ ] Add configurable keyboard shortcuts
* [ ] Improve error handling
* [ ] Add chapter-based summaries
* [ ] Add support for YouTube Shorts

## 🤝 Contributing

Contributions, bug reports and suggestions are welcome.

If you find an issue caused by a change in YouTube or Gemini, please open an issue with:

* Browser and version
* Userscript manager
* Script version
* Description of the problem
* Relevant console errors, if available

## 📄 License

This project is open source. See the `LICENSE` file for details.
