# TurnVoice

A command-line tool that replace voices in youtube videos and can also translate.

## Installation 

```
pip install turnvoice
```

For faster rendering prepare your [CUDA](https://pytorch.org/get-started/locally/) environment:

**CUDA 11.8:**
```
pip install torch==2.1.1+cu118 torchaudio==2.1.1+cu118 --index-url https://download.pytorch.org/whl/cu118
```

**CUDA v12.1:**
```
pip install torch==2.1.1+cu118 torchaudio==2.1.1+cu211 --index-url https://download.pytorch.org/whl/cu211
```

## Usage

```bash
turnvoice -u <YouTube Video URL> -rw <Reference WAV File> -ov <Output Video Filename>
```

### Parameters Explained:

- `-u`, `--url`: (required) The YouTube video URL you want to transform
- `-l`, `--language`: Language to translate to (supported: en, es, fr, de, it, pt, pl, tr, ru, nl, cs, ar, zh, ja, hu, ko)
- `-dd`, `--download_directory`: Where to save the video downloads (default: 'downloads')
- `-sd`, `--synthesis_directory`: Where to save the text to speech audio files (default: 'synthesis')
- `-e`, `--extract`: Use with -e to extract audio directly from the video (may lead to lower quality but can reduce likelihood of errors)
- `-rw`, `--reference_wav`: Your chosen voice in wav format (24kHz, 16 bit, mono, ~10-30s)
- `-ov`, `--output_video`: The grand finale video file name (default: 'final_cut.mp4')

### Example Command:

Ever wanted Arthur Morgan to narrate a cooking tutorial? Here's how:

```bash
turnvoice -u https://www.youtube.com/watch?v=AmC9SmCBUj4 -rw arthur.wav -ov cooking_with_arthur.mp4
```

*This example needs a arthur.wav (or.json) file in the same directory. Works when executed from the tests directory.*

## Pro Tips

### The Art of Choosing a Reference Wav
- A 24000, 44100 or 22050 Hz 16-bit mono wav file of 10-30 seconds is your golden ticket. 
- 24k mono 16 is my default, but I also had voices where I found 44100 32-bit to yield best results
- I test voices [with this tool](https://github.com/KoljaB/RealtimeTTS/blob/master/tests/coqui_test.py) before rendering
- Audacity is your friend for adjusting sample rates. Experiment with frame rates for best results!

### Fixed TTS Model Download Folder
Keep your models organized! Set `COQUI_MODEL_PATH` to your preferred folder.

Windows example:
```bash
setx COQUI_MODEL_PATH "C:\Downloads\CoquiModels"
```

## Future Improvements

- **Optimized Synthesis**: Reducing the synthesis tries for faster results.
- **Voice Cloning from YouTube**: Imagine cloning voices directly from other videos!

## License

TurnVoice is proudly under the [Coqui Public Model License 1.0.0](https://coqui.ai/cpml) and [NLLB-200 CC-BY-NC License](https://huggingface.co/facebook/nllb-200-distilled-600M) (NonCommercial licenses). 

## Let's Make It Fun! 🎉

[Share](https://github.com/KoljaB/TurnVoice/discussions) your funniest or most creative TurnVoice creations with me! 

And if you've got a cool feature idea or just want to say hi, drop me a line on

- [Twitter](https://twitter.com/LonLigrin)  
- [Reddit](https://www.reddit.com/user/Lonligrin)  
- [EMail](mailto:kolja.beigel@web.de)  

Don't forget to leave a star.