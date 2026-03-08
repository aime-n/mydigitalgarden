---
{"dg-publish":true,"permalink":"/tensor-shapes-in-tensor-flow/"}
---


Tensor Shapes in TensorFlow

0️⃣ 0D Tensor (Scalar)
- Shape: `[]`
- Meaning: single value, no axes
- Common uses:
  - loss value → `0.245`
  - learning rate → `0.001`
  - accuracy metric → `0.91`

--------------------------------------------------

1️⃣ 1D Tensor (Vector)
- Shape: `[N]`
- Meaning: list of values along one axis
- Common uses:
  - feature vector → `[age, height, weight]`
  - class logits → `[2.3, 1.1, -0.7]`
  - time series of one signal → `[24]` (24 hourly temps)

--------------------------------------------------

2️⃣ 2D Tensor (Matrix / Batch of vectors)
- Shape: `[rows, cols]`
- Meaning: table of values
- Common uses:
  - dataset → `[32, 10]` (32 samples, 10 features)
  - embedding matrix → `[vocab_size, embed_dim]`
  - grayscale images → `[height, width]`

--------------------------------------------------

3️⃣ 3D Tensor
- Shape: `[A, B, C]`
- Meaning: stack of matrices
- Common uses:
  - time series dataset → `[32, 24, 3]`
    = 32 samples, 24 time steps, 3 sensors
  - sequence embeddings → `[batch, tokens, embed_dim]`
  - video frames (grayscale) → `[frames, H, W]`

--------------------------------------------------

4️⃣ 4D Tensor (very common in deep learning)
- Shape: `[batch, height, width, channels]`
- Common uses:
  - RGB images → `[32, 224, 224, 3]`
  - CNN input tensors
  - feature maps in conv layers

--------------------------------------------------

Rule of thumb:
- 0D → number
- 1D → list
- 2D → table
- 3D → sequence of tables
- 4D → batch of images / spatial data
	- 

