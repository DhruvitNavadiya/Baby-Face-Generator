# Baby-Face-Generator
ComfyUI Workflow(Baby-Face-Generator)

👶 Baby Face Generator (Parent-to-Child Image Generation)

This project demonstrates how to generate a synthetic baby portrait from two parent images using Stable Diffusion + IPAdapter + CLIP Vision inside ComfyUI.
The workflow encodes parent facial features via IPAdapter, blends them, and conditions Stable Diffusion with prompts to produce realistic baby-like outputs.

⚠️ Disclaimer: This is a synthetic AI workflow for demonstration purposes only.
It does not predict actual genetics or real child appearance.

🚀 Features

🧩 ComfyUI Workflow – modular, drag-and-drop nodes for reproducibility.

🔗 IPAdapter + CLIP Vision – encode and blend parent facial features.

🎨 Stable Diffusion – conditioned sampling for realistic baby portraits.

⚙️ Tunable Parameters – control weights, CFG scale, steps, and prompts.

📦 Easy Export – workflow available as JSON + PNG (drag-and-drop).

📂 Project Structure
Baby-Face-Generator/
├── workflow.json        # Importable ComfyUI workflow
├── workflow.png         # Visual workflow (also contains embedded JSON)
├── samples/             # Example baby outputs
│   ├── parentA.png
│   ├── parentB.png
│   ├── sample1.png
│   ├── sample2.png
├── README.md            # Project documentation

🛠️ Requirements

ComfyUI
 (latest build)

Extension: ComfyUI_IPAdapter_plus

Python 3.10+ with:

pip install torch torchvision opencv-python

Models Required

Stable Diffusion 1.5 checkpoint
Place in:

ComfyUI/models/checkpoints/


IPAdapter weights (ip-adapter-full-face_sd15.bin)
Download from IPAdapter Hugging Face
 and place in:

ComfyUI/models/ipadapter/


CLIP Vision backbone (clip-vit-h-14)
Download from laion/CLIP-ViT-H-14
 and place in:

ComfyUI/models/clip_vision/clip-vit-h-14/

🧩 Workflow Explanation
1. Parent Image Processing

Load Image + Resize Image → preprocess parent photos (512×512).

Images are passed into IPAdapter Advanced with the SD checkpoint + adapter model.

2. Model Conditioning

Each IPAdapter Advanced node outputs a model conditioned on one parent face.

Model Merge blends both models (default: 50/50 ratio).

3. Text Prompts

Positive Prompt:

photorealistic baby, 6 months old, soft smooth skin, rounded cheeks, DSLR portrait, natural lighting, high detail


Negative Prompt:

adult face, old person, cartoon, doll, anime, cgi, deformed, blurry, bad anatomy, watermark, text

4. Sampling

KSampler generates the output latent with:

Sampler: Euler a

Steps: 25–30

CFG Scale: 7.0

Seed: random or fixed

5. Output

VAE Decode converts latent → RGB baby portrait.

Optional:

GFPGAN (face restoration)

Real-ESRGAN (upscaling)

🎛️ Tuning Tips

Parent Weights:

Equal (0.5/0.5) → balanced features

Biased (0.6/0.4) → favor one parent

CFG Scale:

6.5–8.0 for realism & prompt adherence

Sampler Steps:

25 for speed, 35–40 for higher detail

Face Restore:

Use GFPGAN strength ~0.3–0.5 (too high makes faces generic)

🖼️ Example Results
Parent A	Parent B	Generated Baby

	
	
📜 Notes

This workflow is designed for AI demo purposes.

It demonstrates skills in workflow engineering, model integration, and prompt tuning using ComfyUI.

It does not provide real genetic predictions.

👨‍💻 Author

Dhruvit Navadiya – AI/ML Engineer
📌 LinkedIn
 | GitHub

