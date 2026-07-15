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

Started on July 5, 2026.

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

### [Editable Scene Simulation for Autonomous Driving via Collaborative LLM-Agents](https://arxiv.org/abs/2402.05746)
- CVPR 2024
- Summary: LLMエージェントを用いて、入力ドライブ動画を入力テキストに基づいて編集する手法を提案。
- Strength: マルチカメラ対応、編集可能、アセットの外挿、言語による編集、Open-Sourceの全てを満たす初めての手法。高品質で有用な編集手法に思える。
- Weakness: 事前定義されたエージェント(e.g. オブジェクト削除エージェント)を利用するため、例えば天候の変更などできず、編集の汎用性は低い。

### [Efficient Video Super-Resolution for Real-time Rendering with Decoupled G-buffer Guidance](https://openaccess.thecvf.com/content/CVPR2025/papers/Zheng_Efficient_Video_Super-Resolution_for_Real-time_Rendering_with_Decoupled_G-buffer_Guidance_CVPR_2025_paper.pdf)
- CVPR 2026
- Summary: G-bufferの各要素を有効に使用するリアルタイムレンダリング向けの動画超解像手法を提案。
- Strength: 技術的新規性に富んでいて、motion vectorで前フレームをワープすると遮蔽部分で整合性が取れなくなるところを、Depthで補助するのが面白いと感じた。またBRDFとNormalは高周波成分のヒントとして活用していて、G-bufferの各要素に明確な役割を分担させている点は、説明可能性が高い。
- Weakness: 60fpsは16msなので、パラメータ32版だとまだレイテンシが高い。

### [VistaDream: Sampling multiview consistent images for single-view scene reconstruction](https://arxiv.org/abs/2410.16892)
- ICCV 2025
- Summary: 単一視点画像からの3DGS再構成手法。最初に周囲を外挿し、その後にwarp-and-inpaintを適用。その後、逆拡散過程で3DGSの学習を含めたサンプリングを行い、多視点一貫性を保持。
- Strength: 手法が直感的で美しい。特に逆拡散過程で3DGSを統合したサンプリングを行うのは合理的。
- Weakness: 逆拡散過程の各ステップで3DGSの更新を行うため、計算コストが高い。

### [Sharp Monocular View Synthesis in Less Than a Second](https://arxiv.org/abs/2512.10685)
- arXiv 2025
- Summary: 1枚の写真を入力とし、3D Gaussianを再構成するSHARPを提案。高速かつ軽量に、実スケールの3DGSを得られる。
- Strength: 軽量に高品質な3DGSが得られるのは魅力的。ネットワークにも技術的知見が多く含まれていて、特に深度補正、ガウシアン補正のアイデアは参考になる。
- Weakness: 初期視点から外れた視点では、外挿ができないため破綻する。論文における評価でも、重なりが60%以上の画像のみ使用しており、新規視点合成タスクとしては弱い。提案手法は、初期視点周りの限られた領域でのみ機能する。

### [FLASHWORLD: HIGH-QUALITY 3D SCENE GENERATION WITHIN SECONDS](https://arxiv.org/abs/2510.13678)
- ICLR 2026 Oral
- Summary: 単一の画像またはテキストプロンプトから数秒で3Dシーンを生成するモデルFlashWorldを提案。
- Strength: 多視点拡散モデルの視覚的クオリティの高さと、3DGSの幾何的整合性の高さの利点を組み合わせた手法を提案している。カメラパスを自由に設定でき、補完したい領域を指定できる。数秒以内に3DGSが生成できるよう、軽量モデルへの知識蒸溜も行われている。
- Weakness: 実際に実行してみると、幾何的整合性が崩れやすく、またボヤけや常識に反したシーン生成が目立っていた。