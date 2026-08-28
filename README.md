# ChitraE

A photo goes in. A painting comes out.

ChitraE is a CycleGAN built to learn artistic style transfer without needing paired training data — it doesn't need the exact same photo painted and unpainted side by side, just two separate collections of images (real photos, and paintings) to learn the transformation between them. Feed it a photograph and it repaints it with the color, texture, and brushwork of the style it learned.

![example](ChitraE/result/test.jpg) → ![example](ChitraE/result/result.jpg)

## Why this exists

Most style-transfer demos stop at "here's a cool filter." ChitraE is built as a foundation — the CycleGAN core, plus a working Flask app around it, so it's a real end-to-end pipeline: train a model, plug it into inference, serve it through a browser. That structure is what makes it extendable later — new styles, new datasets, a cleaner UI, batch processing, whatever direction it grows in.

## What's in here

- **`cyclegan.ipynb` / `cycle.py`** — the CycleGAN itself: generator, discriminator, training loop
- **`inf.py`** — inference + the Flask app that serves it
- **`static/` / `templates/`** — the web front-end
- **`ChitraE_v2.ipynb`, `Demo.ipynb`** — iteration and demo notebooks from development
- **`result/`** — sample input/output pairs

## Running it

```bash
git clone https://github.com/nanda002/ChitraE.git
cd ChitraE/ChitraE
pip install -r requirements.txt
pip install flask flask-wtf
```

Drop the trained weight files in the same folder as `inf.py`, then:

```bash
python inf.py
```

Open the local URL Flask gives you, upload a photo, get your painting back.

## Where this could go

- Support multiple painting styles instead of one fixed style per model
- Swap in a lighter/faster architecture for quicker inference
- Batch upload / process a whole folder of photos at once
- A cleaner front-end — drag-and-drop, before/after slider

## Requirements

TensorFlow / Keras, NumPy, Pandas, Pillow, Matplotlib, Flask, Flask-WTF

---

*Also in this repo: `assignment.ipynb`, an earlier StackGAN experiment (text-to-image bird generation) — a separate exercise, not part of the ChitraE app.*
