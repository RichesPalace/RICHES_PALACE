<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f0c29,50:302b63,100:24243e&height=200&section=header&text=RICHES%20PALACE&fontSize=60&fontColor=ffffff&fontAlignY=38&desc=Twancko%20iQH%20:%20Intelligent%20Quantitative%20Trading&descAlignY=60&descSize=16&animation=fadeIn" width="100%"/>

<br/>

![Model](https://img.shields.io/badge/Model-iQH.3.1-7c3aed?style=for-the-badge&logoColor=white)
![Algorithm](https://img.shields.io/badge/Algorithm-SAC-06b6d4?style=for-the-badge&logoColor=white)
![Pair](https://img.shields.io/badge/Pair-EUR%2FUSD-10b981?style=for-the-badge&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active%20Training-f59e0b?style=for-the-badge&logoColor=white)
![Dev](https://img.shields.io/badge/By-TiQH-ec4899?style=for-the-badge&logoColor=white)

<br/>

> **Model iQH.3.1** : A Soft Actor-Critic reinforcement learning agent built for trading the EUR/USD forex pair.  
> Developed by **Twancko Intelligence Quant Hive (TiQH)** · Advancing intelligent quantitative trading.

</div>

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Model Architecture](#-model-architecture)
- [Training Insights](#-training-insights)
- [Future Directions](#-future-directions)
- [Contributing](#-contributing)

---

## 🧠 Overview

Trading forex, especially major pairs like EUR/USD is notoriously difficult due to high noise, sudden regime changes, and a low signal-to-noise ratio. **Model iQH.3.1** applies the **Soft Actor-Critic (SAC)** algorithm, renowned for stable training in continuous action spaces.

SAC enables the agent to balance:
- 🔍 **Exploration** : trying new actions to discover better strategies
- 🎯 **Exploitation** : leveraging known profitable behaviors

| Property | Value |
|---|---|
| Input Features | ~23 (price history + technical indicators) |
| Output Actions | 5 continuous values (position sizing, direction, etc.) |
| Indicators Used | Moving Averages, MACD, On-Balance Volume |
| Training Stage | Active early-to-mid stage, consistent improvement |

<div align="center">

![Soft-Actor-Critic](https://github.com/user-attachments/assets/b50b54ae-043f-4535-a63b-62f3d3582a27)

*Soft Actor-Critic framework driving model iQH.3.1*

</div>

---

## 🏗 Model Architecture

Model iQH.3.1 uses a compact **feed-forward MLP** with three dense layers optimized for fast training cycles and easy debugging on common hardware.

<div align="center">

<img width="256" alt="iQH Architecture" src="https://github.com/user-attachments/assets/fe07da96-a3e7-45d0-b2f1-782a6a625488" />

*Architecture diagram of model iQH.3.1*

</div>

### Layer Breakdown

```
Input (23 features)
    ↓
Dense Layer 1 → 128 units + activation
    ↓
Batch Normalization (128)
    ↓
Dense Layer 2 → 64 units + activation
    ↓
Batch Normalization (64)
    ↓
Dense Layer 3 → 5 output units + activation
    ↓
Output: 5 continuous SAC actions (dense_17)
```

### Design Rationale

- **~15,000 parameters** : Lightweight for fast iteration; no large hardware required
- **128 → 64 progression** : Stepwise dimensionality reduction preserving key information
- **Batch Normalization** : Counters non-stationarity in forex distributions; prevents vanishing/exploding gradients
- **5-dimensional output** : Encodes mean + log-std for Gaussian actions (position size, directional bias, auxiliary outputs), enabling nuanced decisions beyond simple buy/sell/hold

> ✅ Training so far shows **no crashes, no NaN values, no divergence** the architecture handles noisy financial data well.

---

## 📊 Training Insights

Model iQH.3.1 uses **TensorBoard** to monitor every aspect of training. All graphs below reflect the current training stage and indicate healthy SAC behavior.

<br/>

### 📈 Graph 1 : Running Means & Key Metrics

<img width="1303" alt="TensorBoard Running Means" src="https://github.com/user-attachments/assets/2185b403-6882-4bf3-a6fa-cd467575971e" />

Smooth curves with some values rising from low/negative levels and others decreasing steadily model iQH.3.1 is capturing useful signals in EUR/USD data.

---

### 📉 Graph 2 : Input Features (EUR/USD Indicators)

<img width="1306" alt="TensorBoard EURUSD Features" src="https://github.com/user-attachments/assets/69cabb49-96ac-48c5-a7ab-e90842e2cc3d" />

Curves track target values, MA, MACD, and OBV over time. Visible spikes and trends match real market behavior, confirming the data pipeline feeds correct, varied information.

---

### ⚖️ Graph 3 : Actor & Critic Losses + Entropy

<img width="1298" alt="TensorBoard Losses and Entropy" src="https://github.com/user-attachments/assets/ecff602f-e5f6-48fa-b42d-239b28bbcdf0" />

Actor and critic losses remain **controlled and stable**. Entropy begins high (strong exploration) and decreases gradually exactly how SAC is designed to behave, converging toward confident, reward-maximizing actions.

---

### 🏆 Graph 4 : Performance / Win Rate

<img width="1301" alt="TensorBoard Performance" src="https://github.com/user-attachments/assets/c281e377-8449-4345-b827-2235cd72da08" />

A key performance metric trends **upward** confirming model iQH.3.1 is making progressively better trading decisions.

---

### 🎮 Graph 5 : Predicted Actions Over Time

<img width="1303" alt="TensorBoard Actions" src="https://github.com/user-attachments/assets/70e00275-958a-40c2-968b-37610222ed66" />

Action time-series show initial noise giving way to **emerging structured patterns** — the policy is shifting from random exploration toward learned, deliberate trading choices.

---

## 🔭 Future Directions

Training of model iQH.3.1 is ongoing. Planned upgrades if progress plateaus:

- 🔲 **Larger hidden layers** increased capacity for complex market dynamics
- ⏱ **Temporal components** (LSTM / Transformer layers) capturing longer-range dependencies in price history
- 📦 **Multi-pair expansion** generalizing beyond EUR/USD

---

## 🤝 Contributing

Contributions, questions, and discussions are welcome!

- 🐛 Found a bug? [Open an issue](../../issues)
- 💡 Have an idea? [Submit a pull request](../../pulls)
- 💬 Want to discuss? Start a discussion thread

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=120&section=footer" width="100%"/>

**Developed by Twancko Intelligence Quant Hive (TiQH)**  
*Advancing intelligent quantitative trading.*

</div>
