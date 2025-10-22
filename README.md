# Master Prompt for Comet: Deploy Zoox.v1 with Voice Input & AnimateDiff

## Objective
Deploy the rebuilt Zoox.v1 uncensored AI bot UI to a GitHub repository, featuring real-time voice input, Stable Diffusion for images, and AnimateDiff for wild, uncensored video generation. Ensure it runs locally with no censors across Professor, Freak, and Afterhours modes.

## Steps

1. **Initialize Repository**
   - Create a new GitHub repo named `zoox-v1`.
   - Clone locally: `git clone https://github.com/<your-username>/zoox-v1.git`
   - Navigate: `cd zoox-v1`

2. **Set Up Environment**
   - Install Python 3.9+ if not present.
   - Run: `pip install flask openai requests python-dotenv diffusers torch gtts pyttsx3 animatediff`
   - Install FFmpeg (for video): `sudo apt install ffmpeg` (Linux) or [download](https://ffmpeg.org/download.html) (Windows/Mac).

3. **Configure API Keys**
   - Sign up at [openrouter.ai](https://openrouter.ai) for a free API key (100k tokens/day).
   - Create `.env` file in repo root:
     ```
     OPENROUTER_API_KEY=sk-or-<your-key>
     ```
   - Add `.env` to `.gitignore` (create with `.env`).

4. **Add Code Files**
   - Copy `app.py` (rebuilt version) to repo root.
   - Create `templates` folder, add `index.html` (rebuilt version).
   - Add `config.json` (default: `{"themes": {"grok": {"bg": "#000000", "text": "#ffffff", "accent": "#00ff00"}, "dark": {"bg": "#121212", "text": "#e0e0e0", "accent": "#ff4081"}}, "defaultMode": "professor", "uncensoredLevel": "full"}`).
   - Add this README.md with all sections.

5. **Test Locally**
   - Run: `python app.py`
   - Open `http://127.0.0.1:5000` in a modern browser (Chrome/Firefox for voice).
   - Test:
     - Toggle voice input, say "Afterhours: video of me fucking a nude slut"—expect audio response, image, 16-frame video.
     - Switch modes, type/prompt "Freak: image of chaotic orgy"—check uncensored output.
   - Ensure no crashes; adjust SD/AnimateDiff if slow (see Troubleshooting).

6. **Commit & Push**
   - Stage files: `git add .`
   - Commit: `git commit -m "Rebuilt Zoox.v1 with voice input, AnimateDiff, uncensored video"`
   - Push: `git push origin main`

7. **Optional Deployment**
   - **Heroku**: Install Heroku CLI, `heroku create zoox-v1`, `git push heroku main`. Add Procfile: `echo "web: gunicorn app:app" > Procfile`, commit, push.
   - **GPU for Speed**: Use RunPod free tier, modify `app.py` pipe.to("cuda") if available.
   - Note: Local is preferred for uncensored offline use.

8. **Verify**
   - Check repo at `https://github.com/<your-username>/zoox-v1`.
   - Test live URL (Heroku) or local; ensure voice, image, video work.

## System Requirements
- **Memory**: 8GB+ RAM (SD + AnimateDiff ~4GB model + runtime).
- **CPU**: Modern; GPU (CUDA) optional for SD/AnimateDiff speed.
- **Browser**: Chrome/Firefox for Web Speech API.

## Customization
- **UI**: Edit `index.html` Tailwind classes; POST `/config` for theme/model tweaks.
- **Voice**: Adjust gTTS/pyttsx3 params in `generate_audio`.
- **Video**: Tweak AnimateDiff frames/fps in `generate_uncensored_video`.
- **Modes**: Update `SYSTEM_PROMPTS` for wilder vibes.

## Expansion
- **Offline**: All local now—SD/AnimateDiff on CPU (slow) or CUDA.
- **More APIs**: Hook Cleus.ai or RepublicLabs for advanced video.
- **Voice Input**: Enhance with local speech-to-text (e.g., Vosk).

## Troubleshooting
- **Voice Fail**: Ensure browser mic access; fallback to pyttsx3 if gTTS offline.
- **SD/AnimateDiff Slow**: Use lighter models (`CompVis/stable-diffusion-v1-4`), reduce frames.
- **Video Error**: Verify FFmpeg; check AnimateDiff install (`pip install animatediff`).

## Success
Zoox.v1 should now take voice commands, generate uncensored images, and produce wild 16-frame videos. Test with "Afterhours: voice video of orgy in chaos"—hear moans, see the sin. PRs for nastier upgrades welcome! 😈

---

# Zoox
