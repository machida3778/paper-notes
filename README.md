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
- Weakness: 実際に実行してみると、幾何的整合性が崩れやすく、またボヤけや常識に反したシーン生成が目立っていた。恐らく深度情報を明示的に使用していないためである。

### [STABLE VIRTUAL CAMERA: Generative View Synthesis with Diffusion Models](https://arxiv.org/abs/2503.14489)
- ICCV 2025
- Summary: 明示的3D情報を使用せずに多視点拡散モデルによるNVSを実現するSEVAを提案。
- Strength: 大きな視点変化と小さな視点変化の両方に対応できるような学習方法、および長軌道NVSのための2パスサンプリングにより、明示的3D情報をせずとも高品質なNVSが実現できることを示している。
- Weakness: 技術的新規性はそこまで大きくない。既存手法の組み合わせにより強化されたモデルアーキテクチャと、学習方法およびサンプリング方法を工夫したら、上手くいくことを示したに過ぎない。また、もちろん明示的に3D情報を使用していないので、幾何的な破綻もしやすい（ただ、私が試した中ではかなり高品質だった）。

### [ROFORMER: ENHANCED TRANSFORMER WITH ROTARY POSITION EMBEDDING](https://arxiv.org/pdf/2104.09864)
- Neurocomputing, Volume 568
- Summary: 従来の位置埋め込みはトークン埋め込みに位置ベクトルを加算する方式だった。これに対しRoPEは、Attention内のクエリとキーを、各トークンの絶対位置に比例した角度だけ回転させる。すると内積には相対位置だけが残る、という乗算型の手法である。
- Strength: 相対位置を自然に組み込めて、線形注意とも両立する。事前学習の収束が速く、長文タスクで性能が向上した。
- Weakness: 収束が速い理由と、長文に強い理由を理論的に説明できていない。また、下流タスク（GLUE）での改善は限定的で、比較条件にも疑問が残る。

### [Scaling Rectified Flow Transformers for High-Resolution Image Synthesis](https://arxiv.org/pdf/2403.03206)
- ICML 2024
- Summary: 
Summary: Rectified Flowの学習時のタイムステップ分布を中間重視に変え、さらにテキストと画像で別々の重みを持ちつつattentionのみを結合して双方向に情報を流すMM-DiTを提案。
Strength: 61通りの定式化を統一的な枠組みで公平に比較した大規模な検証が丁寧。logit-normalという単純な変更で、サンプリングステップ数や指標によらず安定して性能が向上し、少ないステップでの劣化も小さい。
Weakness: MM-DiTはモダリティごとの重みにより、パラメータ数と計算コストが増える。

### [FLUX.1 Kontext: Flow Matching for In-Context Image Generation and Editing in Latent Space](https://arxiv.org/pdf/2506.15742)
- arXiv 2025
- Summary: 画像生成と画像編集を単一モデルで扱うFLUX.1 Kontextを提案。参照画像の潜在トークンを生成対象のトークン列に連結し、3D RoPEの時間軸にオフセットを与えて区別するだけで、通常のflow matching損失のまま編集を学習
- Strength: 手法がシンプル。蒸留による少ステップ化で計算コストを下げ、競合より最大1桁高速なため、対話的な反復編集に実用的。複数回の編集でもキャラクターの同一性が崩れにくい。
- Weakness: 技術的新規性は小さい。土台はMMDiT系の既存アーキテクチャ（FLUX.1）で、画像トークンを並べて文脈にする発想もOmniGenやIn-context LoRAなどに見られる。

### [Qwen-Image Technical Report](https://arxiv.org/pdf/2508.02324)
- arXiv 2025
- Summary: 複雑なテキストレンダリング（特に中国語）と一貫性のある画像編集を実現する画像生成基盤モデル。Qwen2.5-VL、VAE、MMDiTで構成され、T2I・TI2I・I2Iのマルチタスク学習で意味と見た目の一貫性を両立。
- Strength: データ作成から学習戦略まで細部にこだわっており、それが品質に寄与している。
- Weakness: MSRoPEなど一部を除き、MMDiTやQwen2.5-VLなど既存技術の組み合わせであり、技術的新規性は薄い（技術レポートのため）。

### [InfiniteYou: Flexible Photo Recrafting While Preserving Your Identity](https://arxiv.org/abs/2503.16418)
- ICCV 2025 (Highlight)
- Summary: 1枚の顔画像とテキストから、本人性を保った人物画像を生成するFLUX向けの手法。ControlNetを一般化したInfuseNetが顔特徴を残差接続でDiTに注入
- Strength: IPA方式の副作用を指摘し、ControlNet型の残差注入というシンプルな設計で回避。ベースモデルを固定するため既存プラグインと併用しやすい。プラグインの効果を本体に焼き込む多段階学習戦略も参考になる。
- Weakness: InfuseNetは本体の約1/4のDiTブロックを持つため、IPAやPuLID-FLUXのような軽量アダプタと比べて計算コストが高い。

### [Human Mesh Modeling for Anny Body](https://arxiv.org/abs/2511.03589)
- ECCV 2026
- Sumamry: スキャン不要で解釈可能なパラメトリック3D人体モデルAnnyを提案。年齢・性別・体重などの表現型パラメータで、乳児から高齢者までを単一モデルで表現
- Strength: 各パラメータが年齢・体重などの意味を持ち、直接制御できるため解釈しやすい。3Dスキャンではなくアーティスト作の人体モデルを用いることで、スキャン収集のコストとプライバシーの問題を回避
- Weakness: 基盤となるMakeHumanの表現型はアーティストのステレオタイプを含むため、Annyも依然としてそれを引き継ぐ

### [ContextDrag: Precise Drag-Based Image Editing via Context-Preserving Token Injection and Position-Aligned Attention](https://arxiv.org/pdf/2512.08477)
- arXiv 2026
- Summary: 点の指定で画像中の物体を移動・変形させるドラッグ編集を、FLUX-Kontextなどのモデル上で、インバージョンやファインチューニングなしに実現する手法。VAEでエンコードした参照画像のトークンをドラッグ先へ注入し(CTI)、そのRoPE位置を移動先に付け替え(PRE)、移動先で衝突する参照トークンをマスクする(OAM)。
- Strength: インバージョンを使わずクリーンなVAE特徴を注入するため、テクスチャを保ったまま正確に編集できる。学習の必要が無い。
- Weakness: 本質的には、潜在空間上でトークンとそのRoPE位置をドラッグ先へ移動させる「潜在空間でのwarp-and-inpaint」である。ピクセル空間でワープした画像を参照としてFLUX-Kontextに入力するという単純なベースラインとの比較がなく、トークン空間で操作することの優位性が十分に示されていない。

### [RoPEMover: Depth-Aware Object Relocation via Positional Embeddings](https://arxiv.org/pdf/2606.27332)
- arXiv 2026
- Summary: 単一画像中の物体を、ドラッグと拡大縮小の指定に基づいて移動させる手法。物体トークンのRoPE位置を移動先へワープし、さらに移動後の深度マップを合成してRoPEの未使用の時間軸に注入することで、前後関係を考慮した移動を実現
- Strength: 事前学習済みDiTの位置表現を書き換えるという単純な仕組みで、正確な位置制御と、影や反射まで含めた物理的に一貫した編集を両立
- Weakness: 深度を時間軸に注入する効果の検証が弱い

### [Untwisting RoPE: Frequency Control for Shared Attention in DiTs](https://arxiv.org/abs/2602.05013)
- arXiv 2026
- Summary: DiTにおける共有アテンションで生じる参照コピーの原因を、RoPEの高周波成分が空間的に同じ位置の参照トークンへアテンションを偏らせることにあると分析。これに基づき、参照画像のキーのRoPEチャンクごとに倍率を掛け、高周波を弱めて低周波を強める周波数考慮型の変調を提案し、内容をコピーせずにスタイルを転写
- Strength: RoPEの周波数構造という観点からコピーの原因を理論と可視化で説明しており、手法もその分析から自然に導かれていて納得感がある。学習不要
- Weakness: 評価がFlux系のモデルに限られており、他のRoPEベースのDiTや動画生成モデルでの有効性は不明

