# Video Generation Survey

A survey of video generation that covers the whole field:

**[Monthly updates →](UPDATES.md)** what changed in the field, month by month since July 2025.

*Industry and resource lists below were last checked on 2026-10-15. This field changes monthly, so check
the live leaderboards for current rankings.*

## Where the field stands (October 2026)

- **Closed models with native audio lead the leaderboards.** Google's Gemini Omni Flash (announced at I/O,
  May 2026), Kuaishou's Kling 3.0 (February 2026) and ByteDance's Seedance 2.0 sit at or near the top of
  public arenas. The order changes with each snapshot and depends on whether audio is scored.
- **OpenAI shut down Sora.** OpenAI announced on 24 March 2026 that the Sora app and API would close, citing
  compute demand and a shift toward world-simulation research.
- **Open weights are close behind.** Lightricks' LTX-2 (open weights, January 2026) generates audio and video
  together; Alibaba's Wan 2.2 (Apache 2.0) and Tencent's HunyuanVideo 1.5 are the other main open models.
- **World models are the next frontier.** Google DeepMind's Genie 3 generates explorable worlds in real time.
  World Labs, Decart and Odyssey build interactive and 3D world generators.

## Seminal papers: a reading timeline

A short list of the papers that changed the direction of the field, from its start to today.
Read them in order and you will see how each idea led to the next. Dates are first arXiv versions.

### Read first: the building blocks (not video-specific)

| Year | Paper | Why read it |
|---|---|---|
| 2013 | [Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114) (Kingma & Welling) | The VAE: learning a compressed latent space. Every modern video model uses one. |
| 2014 | [Generative Adversarial Networks](https://arxiv.org/abs/1406.2661) (Goodfellow et al.) | The GAN: a generator trained against a critic. Drove video generation until 2021. |
| 2020 | [Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239) (Ho et al.) | Diffusion made practical: generate by removing noise step by step. |
| 2020 | [Taming Transformers for High-Resolution Image Synthesis](https://arxiv.org/abs/2012.09841) (Esser et al.) | VQGAN: turns images into discrete tokens that a transformer can predict. |
| 2021 | [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/abs/2112.10752) (Rombach et al.) | Run diffusion in a compressed latent space (Stable Diffusion). The recipe all video diffusion models build on. |
| 2022 | [Classifier-Free Diffusion Guidance](https://arxiv.org/abs/2207.12598) (Ho & Salimans) | The standard trick for making outputs follow the text prompt. |
| 2022 | [Flow Matching for Generative Modeling](https://arxiv.org/abs/2210.02747) (Lipman et al.) | A simpler training objective than diffusion, used by most 2024–2026 video models. |
| 2022 | [Scalable Diffusion Models with Transformers](https://arxiv.org/abs/2212.09748) (Peebles & Xie) | DiT: replaces the U-Net with a transformer. The backbone of Sora-era models. |

### 2014–2017: learning to predict the next frames

| Year | Paper | Why read it |
|---|---|---|
| 2014 | [Video (language) modeling: a baseline for generative models of natural videos](https://arxiv.org/abs/1412.6604) (Ranzato et al.) | One of the first deep generative models of natural video: treats video like language. |
| 2015 | [Unsupervised Learning of Video Representations using LSTMs](https://arxiv.org/abs/1502.04681) (Srivastava et al.) | LSTM encoder-decoder that reconstructs and predicts frames. |
| 2015 | [Convolutional LSTM Network](https://arxiv.org/abs/1506.04214) (Shi et al.) | ConvLSTM: the standard recurrent block for video prediction for years. |
| 2015 | [Deep multi-scale video prediction beyond mean square error](https://arxiv.org/abs/1511.05440) (Mathieu et al.) | Shows why predicted frames come out blurry, and fixes it with an adversarial loss. |
| 2016 | [Unsupervised Learning for Physical Interaction through Video Prediction](https://arxiv.org/abs/1605.07157) (Finn et al.) | Action-conditioned video prediction for robots: an early "world model". |
| 2016 | [Video Pixel Networks](https://arxiv.org/abs/1610.00527) (Kalchbrenner et al.) | First autoregressive video model, generating pixel by pixel. |
| 2017 | [Stochastic Variational Video Prediction](https://arxiv.org/abs/1710.11252) (Babaeizadeh et al.) | SV2P: uses a VAE so the model can predict several possible futures. |

### 2016–2020: the GAN era

| Year | Paper | Why read it |
|---|---|---|
| 2016 | [Generating Videos with Scene Dynamics](https://arxiv.org/abs/1609.02612) (Vondrick et al.) | VGAN: the first GAN that generates video, separating foreground and background. |
| 2016 | [Temporal Generative Adversarial Nets](https://arxiv.org/abs/1611.06624) (Saito et al.) | TGAN: separate generators for time and for each frame. |
| 2017 | [MoCoGAN: Decomposing Motion and Content](https://arxiv.org/abs/1707.04993) (Tulyakov et al.) | Splits "what is in the video" from "how it moves". A key idea that keeps returning. |
| 2017 | [Super SloMo](https://arxiv.org/abs/1712.00080) (Jiang et al.) | Frame interpolation: creating in-between frames for slow motion. |
| 2018 | [Stochastic Video Generation with a Learned Prior](https://arxiv.org/abs/1802.07687) (Denton & Fergus) | SVG: a cleaner way to model uncertain futures. |
| 2018 | [Video-to-Video Synthesis](https://arxiv.org/abs/1808.06601) (Wang et al.) | vid2vid: turns segmentation maps or poses into realistic video. |
| 2018 | [Towards Accurate Generative Models of Video: A New Metric & Challenges](https://arxiv.org/abs/1812.01717) (Unterthiner et al.) | FVD: the metric almost every video paper still reports. |
| 2019 | [Adversarial Video Generation on Complex Datasets](https://arxiv.org/abs/1907.06571) (Clark et al.) | DVD-GAN: scaled GANs to Kinetics. The high point of video GANs. |
| 2020 | [First Order Motion Model for Image Animation](https://arxiv.org/abs/2003.00196) (Siarohin et al.) | Animate any face or body photo from a driving video. |
| 2020 | [A Lip Sync Expert Is All You Need](https://arxiv.org/abs/2008.10010) (Prajwal et al.) | Wav2Lip: accurate lip sync from audio. The base of talking-head work. |

### 2021–2022: tokens, transformers and the first diffusion video models

| Year | Paper | Why read it |
|---|---|---|
| 2021 | [VideoGPT](https://arxiv.org/abs/2104.10157) (Yan et al.) | Compress video to tokens with a VQ-VAE, then predict them with a GPT. |
| 2021 | [StyleGAN-V](https://arxiv.org/abs/2112.14683) (Skorokhodov et al.) | Treats video as a continuous signal in time; strong long-video GAN. |
| 2022 | [Video Diffusion Models](https://arxiv.org/abs/2204.03458) (Ho et al.) | The first video diffusion model. The start of the current era. |
| 2022 | [CogVideo](https://arxiv.org/abs/2205.15868) (Hong et al.) | Large open text-to-video transformer built on a pretrained image model. |
| 2022 | [Make-A-Video](https://arxiv.org/abs/2209.14792) (Singer et al.) | Text-to-video without paired text-video data: learn appearance from images, motion from video. |
| 2022 | [Imagen Video](https://arxiv.org/abs/2210.02303) (Ho et al.) | A cascade of diffusion models for high-definition text-to-video. |
| 2022 | [Phenaki](https://arxiv.org/abs/2210.02399) (Villegas et al.) | Variable-length video from a sequence of prompts, using masked tokens. |
| 2022 | [MAGVIT](https://arxiv.org/abs/2212.05199) (Yu et al.) | Masked token model and a strong 3D video tokenizer. |
| 2022 | [Tune-A-Video](https://arxiv.org/abs/2212.11565) (Wu et al.) | Turns an image diffusion model into a video editor with one example. |

### 2023: latent video diffusion goes mainstream

| Year | Paper | Why read it |
|---|---|---|
| 2023 | [Structure and Content-Guided Video Synthesis](https://arxiv.org/abs/2302.03011) (Esser et al.) | Runway Gen-1: edit a video's style while keeping its structure. |
| 2023 | [Align your Latents](https://arxiv.org/abs/2304.08818) (Blattmann et al.) | Video LDM: add temporal layers to an image latent diffusion model. The standard recipe for two years. |
| 2023 | [AnimateDiff](https://arxiv.org/abs/2307.04725) (Guo et al.) | A plug-in motion module that animates any personalised image model. |
| 2023 | [Language Model Beats Diffusion: Tokenizer is Key](https://arxiv.org/abs/2310.05737) (Yu et al.) | MAGVIT-v2: shows that a good tokenizer lets token models compete with diffusion. |
| 2023 | [Stable Video Diffusion](https://arxiv.org/abs/2311.15127) (Blattmann et al.) | Open model plus a detailed account of data curation for video training. |
| 2023 | [VBench](https://arxiv.org/abs/2311.17982) (Huang et al.) | The most-used benchmark suite, scoring 16 separate quality dimensions. |
| 2023 | [W.A.L.T: Photorealistic Video Generation with Diffusion Models](https://arxiv.org/abs/2312.06662) (Gupta et al.) | A transformer on a shared image-video latent space: a step toward Sora-style models. |
| 2023 | [VideoPoet](https://arxiv.org/abs/2312.14125) (Kondratyuk et al.) | An LLM that generates video and audio tokens: the main alternative to diffusion. |

### 2024: the Sora year, scaling and world models

| Year | Paper | Why read it |
|---|---|---|
| 2024 | [Lumiere](https://arxiv.org/abs/2401.12945) (Bar-Tal et al.) | Generates the whole clip at once in space and time, instead of keyframes then filling in. |
| 2024 | [Video generation models as world simulators](https://openai.com/index/video-generation-models-as-world-simulators/) (OpenAI, Sora report) | DiT on space-time patches at scale. Reset what people expected video models to do. |
| 2024 | [Genie: Generative Interactive Environments](https://arxiv.org/abs/2402.15391) (Bruce et al.) | Learns playable worlds and actions from unlabelled videos. |
| 2024 | [Diffusion Forcing](https://arxiv.org/abs/2407.01392) (Chen et al.) | Mixes next-token prediction with diffusion: each frame gets its own noise level. Basis of long and streaming video. |
| 2024 | [CogVideoX](https://arxiv.org/abs/2408.06072) (Yang et al.) | Strong open DiT text-to-video model with a 3D VAE. |
| 2024 | [Diffusion Models Are Real-Time Game Engines](https://arxiv.org/abs/2408.14837) (Valevski et al.) | GameNGen: a diffusion model that runs the game DOOM in real time. |
| 2024 | [Movie Gen](https://arxiv.org/abs/2410.13720) (Polyak et al.) | Meta's detailed report: flow matching, scaling, video plus synchronised audio. |
| 2024 | [HunyuanVideo](https://arxiv.org/abs/2412.03603) (Kong et al.) | A large open model with a full description of the training system. |
| 2024 | [From Slow Bidirectional to Fast Autoregressive Video Diffusion](https://arxiv.org/abs/2412.07772) (Yin et al.) | CausVid: distils a slow model into a fast frame-by-frame one for streaming. |

### 2025–2026: open frontier models, real-time video and audio

| Year | Paper | Why read it |
|---|---|---|
| 2025 | [Cosmos World Foundation Model Platform for Physical AI](https://arxiv.org/abs/2501.03575) (NVIDIA) | Video world models trained for robotics and driving. |
| 2025 | [Wan](https://arxiv.org/abs/2503.20314) (Team Wan, Alibaba) | The leading open-weight model family, with a full technical report. |
| 2025 | [Self Forcing](https://arxiv.org/abs/2506.08009) (Huang et al.) | Fixes the train-test gap in frame-by-frame video, enabling real-time generation. |
| 2025 | [Video models are zero-shot learners and reasoners](https://arxiv.org/abs/2509.20328) (Wiedemer et al.) | Shows Veo 3 solving many vision tasks it was never trained for. |
| 2026 | [LTX-2](https://arxiv.org/abs/2601.03233) (HaCohen et al.) | Open model that generates audio and video together. |

## Main players

### Closed models and products

| Company | Product / model family | Link |
|---|---|---|
| Google DeepMind | Gemini Omni, Veo, Flow (filmmaking tool) | [models](https://deepmind.google/models/) · [Veo](https://deepmind.google/models/veo/) · [Flow](https://labs.google/flow) |
| Kuaishou | Kling | [klingai.com](https://klingai.com) |
| ByteDance Seed | Seedance (app: Dreamina) | [seed.bytedance.com](https://seed.bytedance.com) · [Dreamina](https://dreamina.capcut.com) |
| Runway | Gen series, Act, Aleph | [runwayml.com](https://runwayml.com) |
| MiniMax | Hailuo | [hailuoai.video](https://hailuoai.video) |
| Luma AI | Ray, Dream Machine | [lumalabs.ai](https://lumalabs.ai) |
| Shengshu | Vidu | [vidu.com](https://www.vidu.com) |
| Pika | Pika | [pika.art](https://pika.art) |
| PixVerse | PixVerse | [pixverse.ai](https://pixverse.ai) |
| Midjourney | Midjourney Video | [midjourney.com](https://www.midjourney.com) |
| Adobe | Firefly Video | [firefly.adobe.com](https://firefly.adobe.com) |
| xAI | Grok Imagine | [x.ai](https://x.ai) |
| Black Forest Labs | FLUX | [bfl.ai](https://bfl.ai) |
| Moonvalley | Marey (trained on licensed data) | [moonvalley.com](https://moonvalley.com) |
| OpenAI | Sora (app and API shut down in 2026) | [openai.com/sora](https://openai.com/sora) |

### Open-weight models

| Developer | Model | Link |
|---|---|---|
| Alibaba | Wan | [wan.video](https://wan.video) · [GitHub](https://github.com/Wan-Video) |
| Tencent | HunyuanVideo | [GitHub](https://github.com/Tencent-Hunyuan) |
| Lightricks | LTX-Video, LTX-2 | [ltx.io](https://ltx.io) · [GitHub](https://github.com/Lightricks) |
| Genmo | Mochi | [genmo.ai](https://www.genmo.ai) |
| Stability AI | Stable Video Diffusion | [stability.ai](https://stability.ai) |
| Meta | Movie Gen (research, not released as weights) | [Movie Gen](https://ai.meta.com/research/movie-gen/) |

Check each model's licence before use. Some open-weight licences exclude certain regions or require a
commercial licence above a revenue threshold.

### World models and interactive video

| Company | Focus | Link |
|---|---|---|
| Google DeepMind | Genie (real-time explorable worlds) | [Genie](https://deepmind.google/models/genie/) |
| NVIDIA | Cosmos (world foundation models for robotics and driving) | [Cosmos](https://www.nvidia.com/en-us/ai/cosmos/) |
| World Labs | Marble (3D world generation) | [worldlabs.ai](https://www.worldlabs.ai) |
| Decart | Real-time interactive video | [decart.ai](https://decart.ai) |
| Odyssey | Interactive video worlds | [odyssey.world](https://odyssey.world) |

### Avatars and talking video

| Company | Link |
|---|---|
| Synthesia | [synthesia.io](https://www.synthesia.io) |
| HeyGen | [heygen.com](https://www.heygen.com) |
| Higgsfield | [higgsfield.ai](https://higgsfield.ai) |

## Track the rankings

| Leaderboard | What it measures | Link |
|---|---|---|
| Artificial Analysis Video Arena | Blind human votes, text-to-video and image-to-video, with and without audio | [leaderboard](https://artificialanalysis.ai/video/leaderboard/text-to-video) |
| Arena (formerly LMArena) | Blind human votes, text-to-video | [leaderboard](https://arena.ai/leaderboard/video/text-to-video) |
| VBench | Automatic scores on 16+ quality dimensions | [leaderboard](https://huggingface.co/spaces/Vchitect/VBench_Leaderboard) |

## Blogs and research pages to follow

| Source | Why follow it | Link |
|---|---|---|
| Google DeepMind blog | Veo, Gemini Omni and Genie announcements | [blog](https://deepmind.google/discover/blog/) |
| Runway Research | Research notes behind the Gen models and world models | [research](https://runwayml.com/research) |
| Meta AI blog | Movie Gen and video research | [blog](https://ai.meta.com/blog/) |
| NVIDIA Research | Cosmos and video-generation papers | [research](https://research.nvidia.com) |
| Hugging Face blog | Open-model releases and how-to guides | [blog](https://huggingface.co/blog) |
| Lilian Weng | Clear long-form explainer: diffusion models for video | [post](https://lilianweng.github.io/posts/2024-04-12-diffusion-video/) |
| Sander Dieleman | Deep explanations of diffusion and generative modelling | [sander.ai](https://sander.ai) |

## Papers: daily feeds and curated lists

| Source | Link |
|---|---|
| Hugging Face Daily Papers | [huggingface.co/papers](https://huggingface.co/papers) |
| arXiv computer vision, new submissions | [arxiv.org/list/cs.CV/new](https://arxiv.org/list/cs.CV/new) |
| Awesome Video Diffusion (Show Lab) | [GitHub](https://github.com/showlab/Awesome-Video-Diffusion) |
| Awesome Video Diffusion Models | [GitHub](https://github.com/ChenHsing/Awesome-Video-Diffusion-Models) |

## Newsletters

| Newsletter | Style | Link |
|---|---|---|
| The Batch (DeepLearning.AI) | Weekly news with context | [the-batch](https://www.deeplearning.ai/the-batch/) |
| Import AI (Jack Clark) | Weekly research and policy | [jack-clark.net](https://jack-clark.net) |
| TLDR AI | Daily, short, technical | [tldr.tech/ai](https://tldr.tech/ai) |
| AlphaSignal | Weekly, for ML researchers | [alphasignal.ai](https://alphasignal.ai) |
| Turing Post | Weekly, includes open-model roundups | [turingpost.com](https://www.turingpost.com) |
