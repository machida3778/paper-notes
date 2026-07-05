# Paper Notes
This repository contains my personal notes on papers in Computer Graphics, Computer Vision, 3D reconstruction, and diffusion-based image generation.

My main research interests are:
- Age Editing
- Image Editing/Generation
- Diffusion Models
- Deep Learning
- LLM Agent
- 3D Scene Reconstruction
- Computer Graphics

## Paper List
### [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
- ICLR 2023
- Summary: LLMを用いて推論の過程とタスク固有の行動を交互に生成する方法を提案。
- Strength: AIエージェントの基礎となる考え方を提案。多様なベンチマークによる検証。
- Weakness: 特定のタスクに特化した専門モデルと比較すると、品質が低い。context windowの不足問題。

### [Data Interpreter: An LLM Agent For Data Science](https://arxiv.org/abs/2402.18679)
- ACL 2025 Findings
- Summary: データサイエンスの問題を解くことに特化したLLMエージェントの枠組みを提案。
- Strength: プログラム可能な動的なノード生成は汎用性が高い。結果もかなり良好に見える。
- Weakness: データサイエンスの問題を解くと言いつつ、簡単な問題しか検証していない。

### [Visual Agentic AI for Spatial Reasoning with a Dynamic API](https://arxiv.org/abs/2502.06787)
- CVPR 2025
- Summary: LLMエージェントを用いてPythonのAPIを生成することで、3D空間関連の問題に対処する手法を提案。テキストと画像を入力し、鏡が20cmなら机は何cmですか？というような問題が対象。
- Strength: 解釈可能なプログラムを生成すること。視覚専門モジュールを活用し、3D空間の把握能力を補う。
- Weakness: oracle versionという視覚モジュールの精度が完璧だった場合のみに既存手法を上回る精度。だが、それはかなり理想的なシチュエーションで、全体的には微妙な結果。

### [Scenethesis: A Language and Vision Agentic Framework for 3D Scene Generation](https://arxiv.org/abs/2505.02836)
- ICLR 2026
- Summary: LLMと画像生成、およびSDFによる物理的一貫性最適化を用いた、テキストから3Dシーンを生成する手法を提案。
- Strength: 結果が良好であり、壁や地面も生成の対象に含まれる。屋内・屋外の両方に対応。
- Weakness: 既存手法を組み合わせたシステム論文であり、技術的新規性に乏しい。関連研究であるCASTを引用していない（SDFベースの物理整合性の補正はCASTが先に提案している）。Objaverseデータセットからオブジェクトを取ってきているため、open-vocabularyではないため、多様性に欠ける。

### [Editable Scene Simulation for Autonomous Driving via Collaborative LLM-Agents]()