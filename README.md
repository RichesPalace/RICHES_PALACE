# RICHES_PALACE
Twancko's iQH


Model iQH.3.1 by Twancko Intelligence Quant Hive (TiQH)
This repository contains the implementation of model iQH.3.1, a Soft Actor-Critic (SAC) reinforcement learning agent built specifically for trading the EUR/USD forex pair. Developed by Twancko Intelligence Quant Hive (TiQH), model iQH.3.1 learns to generate trading decisions using real market data and technical indicators. The project is in the active learning phase, with training still progressing and showing consistent early-to-mid stage signs of improvement.
Project Overview
Trading forex, especially major pairs like EUR/USD, is difficult because of high noise, sudden regime changes, and low signal-to-noise ratio. Model iQH.3.1 applies the SAC algorithm, which is known for stable training in continuous action spaces. SAC helps the agent balance trying new actions (exploration) with using known good actions (exploitation), while maximizing expected rewards.
The state input to model iQH.3.1 consists of approximately 23 features derived from price history and technical indicators (such as Moving Averages, MACD, and On-Balance Volume). The agent outputs 5 continuous values that define trading actions, such as position sizing and direction.



![Soft-Actor-Critic](https://github.com/user-attachments/assets/b50b54ae-043f-4535-a63b-62f3d3582a27)



Model Architecture
Model iQH.3.1 uses a compact feed-forward Multi-Layer Perceptron (MLP) with three dense layers. Below is the exact architecture diagram:
Architecture Diagram of model iQH.3.1
Layer Breakdown

Input: 23 features from processed forex data.

Dense Layer 1: 23 inputs → 128 hidden units + activation function (introduces non-linearity so the model can learn complex patterns).

Batch Normalization (128 units): Normalizes activations to improve training stability.

Dense Layer 2: 128 → 64 hidden units + activation.

Batch Normalization (64 units): Further stabilization.

Dense Layer 3: 64 → 5 output units + activation.

Final Output: Named dense_17 (standard naming), providing 5 continuous values for SAC actions.


<img width="256" height="1216" alt="iQH_Architecture_1" src="https://github.com/user-attachments/assets/fe07da96-a3e7-45d0-b2f1-782a6a625488" />



Why This Architecture for model iQH.3.1?
Model iQH.3.1 starts with a small but capable network (around 15,000 parameters) to enable fast training cycles and easy debugging on common hardware. The 128 → 64 progression reduces dimensionality step-by-step while preserving important information.
Batch Normalization is placed after most dense layers because forex data distributions shift constantly (non-stationary environment). This technique keeps internal activations in a consistent range, reduces training instability, and prevents problems like vanishing or exploding gradients.
The 5-dimensional output aligns perfectly with SAC requirements for continuous control in trading. It commonly represents parameters such as mean and log-standard deviation for two Gaussian actions (e.g., position size and directional bias), plus auxiliary outputs if needed. This allows model iQH.3.1 to make precise, nuanced decisions instead of simple buy/sell/hold choices.
The training so far shows no crashes, no NaN values, and no divergence, which confirms the architecture handles noisy financial data effectively during the ongoing learning process.



Training Insights from TensorBoard
Model iQH.3.1 uses TensorBoard to track every aspect of training. The screenshots below come from the current training stage and reveal healthy progress consistent with SAC behavior in financial environments.


Graph Group 1: Running Means and Key Metrics
TensorBoard Running Means
Smooth curves appear here, with some values rising from low/negative levels and others decreasing steadily. These trends show model iQH.3.1 is capturing useful signals in the EUR/USD data.

<img width="1303" height="576" alt="iQH_tb_graph_1" src="https://github.com/user-attachments/assets/2185b403-6882-4bf3-a6fa-cd467575971e" />


Graph Group 2: Input Features (EUR/USD Indicators)
TensorBoard EURUSD Features
Curves track features like target values, MA, MACD, and OBV over time. The visible spikes and trends match real market behavior, confirming the data pipeline feeds correct, varied information to model iQH.3.1.

<img width="1306" height="575" alt="iQH_tb_graph_2" src="https://github.com/user-attachments/assets/69cabb49-96ac-48c5-a7ab-e90842e2cc3d" />



Graph Group 3: Actor, Critic Losses + Entropy
TensorBoard Losses and Entropy
Actor and critic losses remain controlled and stable. Entropy begins higher (strong exploration) and decreases gradually, which is exactly how SAC is designed to work—moving toward more confident, reward-maximizing actions.


<img width="1298" height="612" alt="iQH_tb_graph_5" src="https://github.com/user-attachments/assets/ecff602f-e5f6-48fa-b42d-239b28bbcdf0" />



Graph Group 4: Performance / Win Rate Curve
TensorBoard Performance
A key metric shows an upward direction. This confirms model iQH.3.1 is making progressively better decisions during the current training phase.

<img width="1301" height="560" alt="iQH_tb_graph_4" src="https://github.com/user-attachments/assets/c281e377-8449-4345-b827-2235cd72da08" />


Graph Group 5: Predicted Actions Over Time
TensorBoard Actions
Action time-series show initial noise but emerging patterns. This indicates the policy of model iQH.3.1 is shifting from random behavior toward structured, learned trading choices.

<img width="1303" height="580" alt="iQH_tb_graph_3" src="https://github.com/user-attachments/assets/70e00275-958a-40c2-968b-37610222ed66" />


Future Directions
Training of model iQH.3.1 will continue. If progress slows at any point, planned upgrades include larger hidden layers or temporal components to handle longer dependencies.
Contributions, questions, and discussions are welcome, open an issue or pull request!
Developed by Twancko Intelligence Quant Hive (TiQH), Advancing intelligent quantitative trading.







