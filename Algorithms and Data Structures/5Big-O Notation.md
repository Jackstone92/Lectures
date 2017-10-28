# Big-O Notation

---

# Motivation
- Compare functions in terms of their growth
  - including functions describing algorithm steps
- Ignore irrelevant details:
  - lower-order terms
  - constant factors
- Basis for informal engineering designs
  - how big will my data grow?
  - will my existing solution still work adequately at scale?

# Big-O (≤)
### `𝑓(𝑥) = 𝑂(𝑔(𝑥)) or𝑓 (𝑥) ∈ 𝑂(𝑔(𝑥))`

### Informally:
- `𝑓(𝑥)` **grows no faster** than `𝑔(𝑥)`

### Heuristically:
- as `𝑥 → ∞, 𝑓(𝑥)` is **bounded above** by some constant times `𝑔(𝑥)`

### Formally:
- **∃(𝐶 ∈ ℝ+) ∶ ∃(𝑥<sub>0</sub> ∈ ℝ) ∶ ∀(𝑥 > 𝑥<sub>0</sub>) ∶ 𝑓(𝑥) < 𝐶𝑔(𝑥)**

### Examples:
- 𝑥<sup>2</sup> − 3𝑥 + 6 = **𝑂(𝑥2)**
  - e.g. choose 𝑥<sub>0</sub> = 1, 𝐶 = 5
- 𝑥<sup>2</sup> − 3𝑥 + 6 = **𝑂(𝑥<sup>4</sup> + 3)**
  - e.g. choose 𝑥<sub>0</sub> = 1, 𝐶 = 2
- 𝑥 + 2𝑥 log(𝑥) + 3(log(𝑥))<sup>2</sup> = **𝑂(𝑥 log(𝑥))**
  - e.g. choose 𝑥<sub>0</sub> = 20, 𝐶 = 3

# Big-Ω (≥)
### `𝑓(𝑥) = Ω(𝑔(𝑥)) or𝑓(𝑥) ∈ Ω(𝑔(𝑥))`

### Informally:
- `𝑓(𝑥)` **grows no slower** than `𝑔(𝑥)`

### Heuristically:
- as `𝑥 → ∞, 𝑓(𝑥)` is **bounded below** by some constant times `𝑔(𝑥)`

### Formally:
- **∃(𝐶 ∈ ℝ+) ∶ ∃(𝑥<sub>0</sub> ∈ ℝ) ∶ ∀(𝑥 > 𝑥<sub>0</sub>) ∶ 𝑓(𝑥) > 𝐶𝑔(𝑥)**

### Examples:
- 𝑥<sup>2</sup> − 3𝑥 + 6 = **Ω(𝑥<sup>2</sup>)**
  - e.g. choose 𝑥<sub>0</sub> = 3, 𝐶 = 1/2
- 𝑥<sup>2</sup> − 3𝑥 + 6 = **Ω(𝑥)**
  - e.g. choose 𝑥<sub>0</sub> = 3, 𝐶 = 1
- 𝑥 + 2𝑥 log(𝑥) + 3(log(𝑥))<sup>2</sup> = **Ω(log(𝑥)<sup>2</sup>)**
  - e.g. choose 𝑥<sub>0</sub> = 1, 𝐶 = 1

# Big-Θ (=)
### `𝑓(𝑥) = Θ(𝑔(𝑥)) or𝑓 (𝑥) ∈ Θ(𝑔(𝑥))`

### Informally:
- `𝑓(𝑥)` **grows like** `𝑔(𝑥)`

### Heuristically:
- as `𝑥 → ∞, 𝑓(𝑥)` is **bounded above and below** by constants times `𝑔(𝑥)`

### Formally:
- **∃(𝐶<sub>1</sub>, 𝐶<sub>2</sub> ∈ ℝ+) ∶ ∃(𝑥<sub>0</sub> ∈ ℝ) ∶ ∀(𝑥 > 𝑥<sub>0</sub>) ∶ 𝐶<sub>1</sub>𝑔(𝑥) < 𝑓(𝑥) < 𝐶<sub>2</sub>𝑔(𝑥)**

### Examples:
- 𝑥<sup>2</sup> − 3𝑥 + 6 = **Θ(𝑥<sup>2</sup>)**
  - e.g. choose 𝑥<sub>0</sub> = 3, 𝐶<sub>1</sub> = 1/2, 𝐶<sub>2</sub> = 5

# Little-o (<)
### `𝑓(𝑥) = 𝑜(𝑔(𝑥)) or𝑓 (𝑥) ∈ 𝑜(𝑔(𝑥))`

### Informally:
- `𝑓(𝑥)` **grows much slower** than `𝑔(𝑥)`

### Heuristically:
- as `𝑥 → ∞, 𝑓(𝑥)/𝑔(𝑥) → 0`

### Formally:
- **∀(𝜀 ∈ ℝ+) ∶ ∃(𝑥<sub>0</sub> ∈ ℝ) ∶ ∀(𝑥 > 𝑥<sub>0</sub>) ∶ 𝑓(𝑥) < 𝜀𝑔(𝑥)**


# Common complexity classes

|  Rank | Time complexity |
|  ---  |       ---       |
|   1.  |       Θ(1)      |
