# Growth of Functions

---

# Motivation
Turning empirical measurements into scaling hypotheses, or *vice versa*

# Common functional classes
1. Power-law
2. Logarithmic and linear-logarithmic
3. Exponential

# Power law
## 𝑓(𝑛) ∝ 𝑛𝑘
## 𝑓(𝑛) = 𝐴𝑛<sup>𝑘</sup>
## Example
Given 𝑓(𝑛<sub>1</sub>) and 𝑓(𝑛<sub>2</sub>), estimate 𝑘 (and 𝐴):
- 𝑓(𝑛<sub>1</sub>) / 𝑓(𝑛<sub>2</sub>) = (𝑛<sub>1</sub>/𝑛<sub>2</sub>)<sup>k</sup>
- 𝑘 = log(𝑓(𝑛<sub>1</sub>)/𝑓(𝑛<sub>2</sub>)) / log(𝑛<sub>1</sub>/𝑛<sub>2</sub>)
- A = 𝑓(𝑛) / 𝑛<sup>k</sup>

# Logarithmic
## 𝑓(𝑛) ∝ log(𝐵𝑛)
## 𝑓(𝑛) = 𝐴 log(𝐵𝑛)
## Example
Given 𝑓(𝑛<sub>1</sub>) and 𝑓(𝑛<sub>2</sub>), estimate 𝐴 (and 𝐵):

- 𝑓(𝑛<sub>1</sub>) − 𝑓(𝑛<sub>2</sub>) = 𝐴(log(𝑛<sub>1</sub>) − log(𝑛<sub>2</sub>))
- 𝐴 = (𝑓(𝑛<sub>1</sub>) − 𝑓(𝑛<sub>2</sub>)) / (log(𝑛<sub>1</sub>) − log(𝑛<sub>2</sub>))
- 𝐵(𝑛) = e<sup>(𝑓(𝑛) / 𝐴)</sup>
- 𝐵 = e<sup>(𝑓(𝑛) / 𝐴)</sup> / 𝑛

# Exponential
## 𝑓(𝑛) ∝ 2<sup>𝑐𝑛</sup>
## 𝑓(𝑛) = 𝐴2<sup>𝑐𝑛</sup>
## Example
Given 𝑓(𝑛<sub>1</sub>) and 𝑓(𝑛<sub>2</sub>), estimate 𝑐 (and 𝐴):
- log(𝑓(𝑛<sub>1</sub>)) − log(𝑓(𝑛<sub>2</sub>)) = 𝑐(𝑛<sub>1</sub> − 𝑛<sub>2</sub>)
- log(𝑓(𝑛<sub>1</sub>) - 𝑓(𝑛<sub>2</sub>)) = 𝑐(𝑛<sub>1</sub> − 𝑛<sub>2</sub>)
- 𝑐 = (log(𝑓(𝑛<sub>1</sub>)) − log(𝑓(𝑛<sub>2</sub>))) / (𝑛<sub>1</sub> − 𝑛<sub>2</sub>)
- 𝐴 = 𝑓(𝑛) / 2<sup>𝑐𝑛</sup>
