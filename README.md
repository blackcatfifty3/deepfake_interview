**System Engineer Interview Demo — Windows and macOS Setup**

This document explains how to install and run local System Engineer interview simulation on either Windows 11 or macOS. The UI is a Zoom-inspired training simulation and does not connect to Zoom.
**What the demo does**
- Whisper.cpp transcribes my spoken question locally.
- Qwen3 1.7B runs through Ollama and generates an answer locally.
- Sarvam Bulbul v4 Flash converts the generated answer text into speech. Internet access and an API key are required for this voice step.
- The meeting-style browser UI shows a simulated camera-permission prompt, fades in my configured candidate photo, requests real microphone permission, and waits for Start Call before listening.
- It intentionally hides transcripts, answer text, and processing captions. The simulated camera prompt does not use the physical camera.
**Which setup guide I use**
- Windows 11: follow README_WINDOWS.md. The Windows installer ZIP also includes the same guide as README.md.
- macOS: follow README_MACOS.md. The macOS installer ZIP also includes the same guide as README.md.

**Requirements on either platform**
I need internet access during first-time setup and for Sarvam voice generation, a working microphone and speakers/headphones, several gigabytes of free disk space, and a valid Sarvam API key from https://dashboard.sarvam.ai/.
The installer downloads the local dependencies and model files. Setup only needs to be completed once per computer; after successful installation, I use the platform-specific launcher for each interview.
**Voice configuration**
The provided config selects:
SARVAM_LANGUAGE_CODE = "en-IN"
SARVAM_SPEAKER = "aayan_hi_conversational"
SARVAM_MODEL = "bulbul:v4-flash"
SARVAM_PACE = 1.0
SARVAM_SAMPLE_RATE = 24000
Aayan is designed for Hindi, so English output may have a Hindi-influenced accent. I can select another available voice from the Sarvam voice catalogue.
**Privacy and API key**
Whisper transcription, Qwen reasoning, and local knowledge lookup run on my computer. Only the generated answer text is sent to Sarvam to synthesize speech. My sarvam.env contains the API key, so I keep it private and never share a configured project folder or publish the key. I distribute only a clean package with an empty placeholder key.
General troubleshooting
- If installation is interrupted, I rerun the platform-specific installer; it reuses components where possible.
- If the model download fails, I check internet access and disk space before rerunning setup.
- If Sarvam returns 401 or 403, I check that the key in sarvam.env is valid and active.
- If Sarvam returns 429, I check the usage limit and credits in the Sarvam dashboard.
- If the microphone is blocked, I enable access both in browser permissions and the operating-system privacy settings where required.
- If the app fails to launch, I follow the troubleshooting section in the platform-specific README.
