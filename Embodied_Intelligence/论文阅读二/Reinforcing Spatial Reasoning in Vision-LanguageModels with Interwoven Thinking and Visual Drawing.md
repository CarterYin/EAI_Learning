### 1 Introduction

**英文**: Large language models (LLMs) have exhibited remarkable reasoning capabilities in complex tasks such as mathematical problem-solving [65, 35] and code generation [6], particularly through the “slow thinking” paradigm exemplified by OpenAI o1 [26] and DeepSeek R1 [10], which enables extended reasoning with in-depth self-reflection.

**中文翻译**: 大型语言模型（LLMs）在复杂任务（如数学问题求解[65, 35]和代码生成[6]）中展现了卓越的推理能力，特别是在“慢思考”范式下，如OpenAI o1 [26] 和 DeepSeek R1 [10] 所示，这种范式通过深入的自我反思实现了扩展推理。

**解读**:  
- **大型语言模型（LLMs）**: 指基于大规模数据集训练的自然语言处理模型，如GPT系列，能够处理复杂的语言任务。  
- **推理能力（reasoning capabilities）**: 指模型通过逻辑分析解决问题的能力，例如解决数学问题或生成代码。  
- **慢思考（slow thinking）**: 借鉴人类认知中的“系统2”思考，指模型在推理时采取更深思熟虑、逐步推导的方式，而不是快速直觉反应。OpenAI o1 和 DeepSeek R1 是采用这种方法的代表模型。  
- **自我反思（self-reflection）**: 模型在推理过程中评估自身输出并进行修正的能力，类似于人类在思考时检查自己的逻辑。  
- **文献引用 [65, 35], [6], [26], [10]**: 这些引用指向相关研究，表明LLMs在数学和代码生成等任务中的成功案例，以及慢思考范式的具体实现。

---

**英文**: Encouraged by the success, a growing body of research is now aiming to adapt similar techniques to large vision-language models (LVLMs) to enhance their capabilities in image and video reasoning [71, 11, 49, 13].

**中文翻译**: 受此成功的鼓舞，越来越多的研究现在致力于将类似技术应用于大型视觉-语言模型（LVLMs），以增强其在图像和视频推理方面的能力[71, 11, 49, 13]。

**解读**:  
- **大型视觉-语言模型（LVLMs）**: 结合视觉和语言处理能力的模型，能够处理图像、视频和文本输入，例如用于图像描述或视觉问答。  
- **图像和视频推理（image and video reasoning）**: 指模型分析图像或视频内容，并结合文本问题进行逻辑推理的能力。  
- **文献引用 [71, 11, 49, 13]**: 这些引用表明已有研究尝试将LLMs的推理技术迁移到LVLMs，但具体成果和局限性将在后文探讨。

---

**英文**: While current LVLMs excel at basic visual perception tasks such as object detection [12] and narrative understanding [40, 9], they often struggle with spatial reasoning [63, 69], which requires understanding spatial relationships among objects and tracking their dynamic evolution [59]—capabilities that are crucial for real-world applications such as robotics [48] and augmented reality [17].

**中文翻译**: 虽然当前的LVLMs在基本视觉感知任务（如目标检测[12]和叙事理解[40, 9]）中表现出色，但它们在空间推理[63, 69]方面常常遇到困难，空间推理需要理解物体之间的空间关系并跟踪其动态演变[59]——这些能力对于现实世界的应用（如机器人技术[48]和增强现实[17]）至关重要。

**解读**:  
- **基本视觉感知任务**: 包括目标检测（识别图像中的物体）和叙事理解（理解图像或视频中的故事性内容）。  
- **空间推理（spatial reasoning）**: 指理解物体在空间中的相对位置、方向及动态变化的能力，例如判断物体A是否在物体B的左侧，或跟踪视频中物体的运动轨迹。  
- **动态演变（dynamic evolution）**: 指物体在时间维度上的位置或状态变化，例如在视频中跟踪移动物体。  
- **现实世界应用**: 机器人需要空间推理来导航和操作物体；增强现实需要精确的空间定位来叠加虚拟内容。  
- **文献引用 [12], [40, 9], [63, 69], [59], [48], [17]**: 这些引用支持LVLMs在感知任务中的成功，同时指出其在空间推理方面的不足，以及空间推理在实际应用中的重要性。

---

**英文**: Indeed, even when such deep visual understanding is required, LVLMs still rely solely on text-based reasoning [71], assuming that visual information can be perfectly translated into textual semantic space [23].

**中文翻译**: 事实上，即使需要深入的视觉理解，LVLMs仍然仅依赖基于文本的推理[71]，假设视觉信息可以完全转化为文本语义空间[23]。

**解读**:  
- **基于文本的推理（text-based reasoning）**: 当前LVLMs通常将图像或视频信息转化为文本描述，然后在文本空间中进行推理。  
- **文本语义空间（textual semantic space）**: 指将视觉信息（如图像中的物体位置）抽象为文本描述的表示空间。  
- **局限性**: 这种转化假设视觉信息可以无损地表达为文本，但实际上，空间细节（如精确的几何关系）在转化中会丢失。  
- **文献引用 [71], [23]**: 这些引用指出文本推理的普遍应用及其局限性。

---

**英文**: Unfortunately, such translation is inherently challenging [33]: spatial details are inevitably lost when converting visual information to text, and describing dynamic changes of object positions becomes prohibitively complex in textual space (see examples of GPT-4o in Figure 1).

**中文翻译**: 不幸的是，这种转化本身具有挑战性[33]：将视觉信息转换为文本时，空间细节不可避免地会丢失，而在文本空间中描述物体位置的动态变化变得极其复杂（见图1中GPT-4o的示例）。

**解读**:  
- **空间细节丢失**: 图像中的精确位置、角度或距离等信息在转化为文本时难以完整保留。  
- **动态变化的复杂性**: 描述视频中物体随时间变化的位置或轨迹需要大量文本，容易导致信息冗余或不准确。  
- **GPT-4o示例（Figure 1）**: 文章提到图1展示了GPT-4o在空间推理任务中的失败案例，可能是因为其仅依赖文本推理，未能有效捕捉空间细节。  
- **文献引用 [33]**: 支持视觉信息到文本转化的固有困难。

---

**英文**: Taking inspiration from human cognition, where spatial reasoning relies on mental visualization and dynamic manipulation [3], we advocate a vision-centric reasoning paradigm where models actively edit and re-encode visual information at each reasoning step, dynamically supplementing spatial details and relationships.

**中文翻译**: 受人类认知的启发，人类的空間推理依赖于心理可视化和动态操作[3]，我们提倡一种以视觉为中心的推理范式，在该范式中，模型在每个推理步骤中主动编辑和重新编码视觉信息，动态补充空间细节和关系。

**解读**:  
- **人类认知（human cognition）**: 人类在空间推理时会在脑海中构建和操作视觉场景，例如想象物体移动的路径。  
- **心理可视化（mental visualization）**: 指在头脑中形成物体的空间图像。  
- **动态操作（dynamic manipulation）**: 指在脑海中调整或重新组织空间信息，例如旋转物体或模拟路径。  
- **以视觉为中心的推理范式（vision-centric reasoning paradigm）**: 提出模型应直接在视觉空间中操作，而不是依赖文本转化，通过编辑图像（如添加标注）来辅助推理。  
- **重新编码（re-encode）**: 指模型在推理过程中更新视觉信息的表示，例如通过绘制边界框来标记物体位置。  
- **文献引用 [3]**: 提供人类空间推理的认知科学依据。

---

**英文**: This “thinking with images” approach, while validated by OpenAI o3 [46], remains underexplored in open-source research.

**中文翻译**: 这种“用图像思考”的方法虽然已被OpenAI o3 [46]验证，但在开源研究中仍未被充分探索。

**解读**:  
- **用图像思考（thinking with images）**: 指直接基于视觉信息进行推理，而非依赖文本描述。  
- **OpenAI o3 [46]**: 可能是OpenAI开发的一种模型，验证了视觉推理的可行性，但具体细节未在开源社区广泛研究。  
- **开源研究（open-source research）**: 指公开共享代码和数据的学术研究，与商业闭源模型（如OpenAI的产品）相对。

---

**英文**: In parallel with our work, recent studies have begun to integrate visual tools to enable vision-centric reasoning [8, 50, 21, 31].

**中文翻译**: 与我们的工作并行，近期研究已开始整合视觉工具以实现以视觉为中心的推理[8, 50, 21, 31]。

**解读**:  
- **视觉工具（visual tools）**: 指用于处理视觉信息的工具，如目标检测系统或光学字符识别（OCR）系统。  
- **文献引用 [8, 50, 21, 31]**: 这些引用指向近期尝试将视觉工具融入LVLMs的研究。

---

**英文**: However, these approaches exhibit limitations along two key dimensions.

**中文翻译**: 然而，这些方法在两个关键维度上存在局限性。

**解读**:  
- **两个关键维度**: 文章接下来会详细说明这些局限性，涉及感知工具的依赖和推理数据的局限。

---

**英文**: First, the reasoning capabilities of LVLMs are constrained by black-box perception tools (e.g., grounding and OCR systems), resulting in not only fixed perception capabilities but also fragmented reasoning composed of disconnected tool invocations that undermine coherence and holistic planning.

**中文翻译**: 首先，LVLMs的推理能力受到黑盒感知工具（例如，定位和OCR系统）的限制，这不仅导致固定的感知能力，还导致推理过程碎片化，由不连贯的工具调用组成，削弱了连贯性和整体规划。

**解读**:  
- **黑盒感知工具（black-box perception tools）**: 指外部预训练的视觉处理系统（如目标检测或OCR），其内部机制不透明，模型无法对其进行优化。  
- **固定感知能力（fixed perception capabilities）**: 这些工具的性能无法随LVLMs的训练而改进，限制了模型的灵活性。  
- **碎片化推理（fragmented reasoning）**: 指推理过程被分割成多个独立的工具调用，缺乏整体性。  
- **连贯性和整体规划（coherence and holistic planning）**: 指推理过程应具有逻辑连续性和全局视角，而非零散的步骤拼接。

---

**英文**: Second, these methods heavily draw upon reasoning data curated based on human priors, which often exhibit oversimplified logic compared to the complexity of spatial reasoning tasks, with problem decomposition and tool invocation interleaved in a simplistic and linear fashion [8, 50].

**中文翻译**: 其次，这些方法在很大程度上依赖于基于人类先验知识整理的推理数据，这些数据的逻辑通常过于简单，与空间推理任务的复杂性相比，问题分解和工具调用以简单线性的方式交织进行[8, 50]。

**解读**:  
- **人类先验知识（human priors）**: 指基于人类经验设计的推理数据，例如预设的推理步骤或工具使用方式。  
- **过于简单的逻辑（oversimplified logic）**: 指现有数据无法充分反映空间推理任务的复杂性，例如动态的空间变化或多视角整合。  
- **问题分解和工具调用（problem decomposition and tool invocation）**: 指将复杂问题拆分为子问题并调用工具解决的策略。  
- **简单线性方式（simplistic and linear fashion）**: 指当前方法按固定顺序调用工具，缺乏灵活性和反思能力。  
- **文献引用 [8, 50]**: 指出现有方法在数据和推理方式上的局限。

---

**英文**: Such adherence to prescribed reasoning patterns prevents LVLMs from developing the capacity for critical reflection on tool outputs—a capability that has proven crucial for advanced reasoning [44].

**中文翻译**: 这种对规定推理模式的坚持，阻碍了LVLMs发展对工具输出的批判性反思能力——这种能力已被证明对高级推理至关重要[44]。

**解读**:  
- **规定推理模式（prescribed reasoning patterns）**: 指预设的、固定的推理步骤，限制了模型的灵活性。  
- **批判性反思（critical reflection）**: 指模型评估和修正工具输出或自身推理过程的能力。  
- **高级推理（advanced reasoning）**: 指能够处理复杂、动态或多模态任务的推理能力。  
- **文献引用 [44]**: 强调反思能力在推理中的重要性。

---

**英文**: These fundamental limitations call for a more flexible and intrinsic approach to vision-centric reasoning.

**中文翻译**: 这些根本性局限性要求一种更灵活和内在的以视觉为中心的推理方法。

**解读**:  
- **灵活和内在（flexible and intrinsic）**: 指推理方法应由模型自身驱动，而不是依赖外部工具或固定的推理模式。  
- **以视觉为中心（vision-centric）**: 强调直接在视觉空间中操作，而非依赖文本转化。

---

**英文**: In light of these challenges, we propose “drawing to reason in space,” a novel, versatile reasoning paradigm that empowers LVLMs to reason through elementary drawing operations, as exemplified in Figure 1.

**中文翻译**: 鉴于这些挑战，我们提出“在空间中通过绘图进行推理”，一种新颖、灵活的推理范式，使LVLMs能够通过基本的绘图操作进行推理，如图1所示。

**解读**:  
- **绘图推理（drawing to reason in space）**: 指通过绘制边界框、辅助线等操作，直接在图像上表达和分析空间关系。  
- **基本绘图操作（elementary drawing operations）**: 包括绘制边界框（标记物体位置）和辅助线（表示空间关系）。  
- **图1（Figure 1）**: 展示了绘图推理的具体示例，强调其与传统文本推理的区别。

---

**英文**: Through simple yet powerful operations, including bounding boxes for object localization and auxiliary lines for relationship analysis, this paradigm enables direct visual interaction for spatial problem-solving, mirroring human behavior while avoiding the pitfalls of dependence on external perception tools.

**中文翻译**: 通过简单但强大的操作，包括用于物体定位的边界框和用于关系分析的辅助线，这一范式实现了直接的视觉交互来解决空间问题，模仿人类行为，同时避免了依赖外部感知工具的缺陷。

**解读**:  
- **边界框（bounding boxes）**: 用于标记图像中物体的位置和范围。  
- **辅助线（auxiliary lines）**: 用于表示物体之间的空间关系，如方向或距离。  
- **直接视觉交互（direct visual interaction）**: 指模型在图像上直接操作，而不是通过文本间接推理。  
- **模仿人类行为（mirroring human behavior）**: 人类在空间推理时常通过绘制草图或标记来辅助思考，模型模仿这一过程。  
- **避免外部工具依赖**: 传统方法依赖黑盒工具，而绘图推理由模型自身完成，更具自主性。

---

**英文**: Based on this paradigm, we develop VILASR, a VIsion-LAnguage model that achieves sophisticated Spatial Reasoning through interwoven thinking and visual drawing.

**中文翻译**: 基于这一范式，我们开发了VILASR，一种视觉-语言模型，通过交织的思考和视觉绘图实现复杂空间推理。

**解读**:  
- **VILASR**: 模型名称，代表“Vision-Language Spatial Reasoning”，强调其在空间推理中的专长。  
- **交织的思考和视觉绘图（interwoven thinking and visual drawing）**: 指模型在推理过程中同时进行逻辑思考和视觉操作，二者相互促进。

---

**英文**: To realize this vision, we develop a three-stage training framework (Figure 2).

**中文翻译**: 为了实现这一愿景，我们开发了一个三阶段训练框架（见图2）。

**解读**:  
- **三阶段训练框架**: 包括冷启动训练、反思性拒绝采样和强化学习，具体在图2中展示。  
- **图2（Figure 2）**: 提供了训练框架的视觉化说明。

---

**英文**: First, we introduce cold-start training with synthetic data to establish basic visual drawing abilities.

**中文翻译**: 首先，我们引入使用合成数据进行冷启动训练，以建立基本的视觉绘图能力。

**解读**:  
- **冷启动训练（cold-start training）**: 在模型训练初期，使用人工生成的合成数据（synthetic data）来初始化能力。  
- **基本视觉绘图能力**: 指模型学会绘制边界框和辅助线等操作。

---

**英文**: Second, we design a reflective rejection sampling mechanism that selectively reinforces reasoning paths demonstrating both correct answers and self-correction behaviors, enabling models to revise their visual operations based on intermediate results.

**中文翻译**: 其次，我们设计了一个反思性拒绝采样机制，选择性地强化那些展示正确答案和自我纠错行为的推理路径，使模型能够根据中间结果修正其视觉操作。

**解读**:  
- **反思性拒绝采样（reflective rejection sampling）**: 通过评估推理路径的质量，选择那些既有正确答案又有自我纠错行为的路径进行训练。  
- **自我纠错行为（self-correction behaviors）**: 模型在推理中检查和修正自己的错误，例如调整错误的边界框。  
- **中间结果（intermediate results）**: 指推理过程中的初步输出，如初始绘制的边界框。

---

**英文**: Finally, we employ reinforcement learning (RL) with carefully designed rewards that balance answer correctness and reasoning format, incentivizing both accurate spatial understanding and coherent visual thinking processes.

**中文翻译**: 最后，我们采用强化学习（RL），使用精心设计的奖励机制平衡答案正确性和推理格式，激励模型实现精确的空间理解和连贯的视觉思考过程。

**解读**:  
- **强化学习（RL）**: 通过优化奖励函数来调整模型行为。  
- **精心设计的奖励（carefully designed rewards）**: 奖励同时考虑答案的正确性（如是否正确识别空间关系）和推理过程的连贯性（如绘图步骤的逻辑性）。  
- **连贯的视觉思考（coherent visual thinking）**: 指推理过程在视觉和逻辑上的一致性。

---

**英文**: Extensive experiments across five diverse spatial reasoning benchmarks demonstrate the effectiveness of VILASR, which achieves substantial improvements over strong baselines by 18.4% on average, involving challenging scenarios that require sequential spatial planning (e.g., maze navigation), temporal relationship tracking (e.g., video-based reasoning), and information integration from multiple perspectives.

**中文翻译**: 跨越五个多样化空间推理基准的广泛实验证明了VILASR的有效性，该模型在强劲基线上平均提升了18.4%，涉及需要顺序空间规划（如迷宫导航）、时间关系跟踪（如基于视频的推理）和多视角信息整合的挑战性场景。

**解读**:  
- **五个空间推理基准**: 包括迷宫导航、视频推理、多视角推理等任务，覆盖静态和动态空间推理。  
- **强劲基线（strong baselines）**: 指现有的高性能LVLMs模型，如GPT-4o。  
- **18.4%提升**: 表明VILASR在性能上显著优于现有方法。  
- **顺序空间规划（sequential spatial planning）**: 指按步骤规划空间路径，如在迷宫中导航。  
- **时间关系跟踪（temporal relationship tracking）**: 指在视频中跟踪物体随时间变化的空间关系。  
- **多视角信息整合（information integration from multiple perspectives）**: 指综合多个图像或视角的信息进行推理。

---

**英文**: Ablation studies reveal the critical role of each training stage.

**中文翻译**: 消融研究揭示了每个训练阶段的关键作用。

**解读**:  
- **消融研究（ablation studies）**: 通过逐一移除或修改训练阶段，评估每个阶段对模型性能的贡献。

---

**英文**: Particularly, reflective rejection sampling significantly enhances the model’s self-correction capabilities, with the frequency of reflection behaviors doubling compared to models trained without this intermediate stage.

**中文翻译**: 特别是，反思性拒绝采样显著增强了模型的自我纠错能力，与没有这一中间阶段训练的模型相比，反思行为的频率翻倍。

**解读**:  
- **自我纠错能力（self-correction capabilities）**: 指模型在推理中发现和修正错误的能力。  
- **反思行为频率翻倍**: 表明反思性拒绝采样显著提高了模型的反思能力。

---

**英文**: Further inference-time scaling experiments reveal that each training stage progressively enhances the model’s reasoning potential, with the final RL optimization effectively consolidating multi-attempt capabilities while maintaining strong single-attempt performance, significantly narrowing the performance gap compared to earlier training stages.

**中文翻译**: 进一步的推理时间扩展实验表明，每个训练阶段逐步增强了模型的推理潜力，最终的强化学习优化有效整合了多次尝试的能力，同时保持了强大的单次尝试性能，显著缩小了与早期训练阶段的性能差距。

**解读**:  
- **推理时间扩展实验（inference-time scaling experiments）**: 指在推理阶段测试模型性能随训练阶段增加的变化。  
- **多次尝试能力（multi-attempt capabilities）**: 指模型通过多次推理尝试提高准确性的能力。  
- **单次尝试性能（single-attempt performance）**: 指模型在首次推理时的准确性。  
- **性能差距（performance gap）**: 指早期训练阶段与最终模型之间的性能差异。

---

**英文**: In summary, our contributions are threefold:

**中文翻译**: 总之，我们的贡献有三个方面：

**解读**: 接下来列出了文章的三大主要贡献。

---

**英文**: I. We propose drawing to reason in space, a novel reasoning paradigm that enables LVLMs to perform spatial reasoning through interpretable visual operations;

**中文翻译**: I. 我们提出在空间中通过绘图进行推理，一种新颖的推理范式，使LVLMs能够通过可解释的视觉操作进行空间推理；

**解读**:  
- **可解释的视觉操作（interpretable visual operations）**: 指绘图操作（如边界框、辅助线）具有明确的逻辑和可追溯性，便于理解模型的推理过程。

---

**英文**: II. We develop a principled training framework that effectively cultivates models’ visual reasoning capabilities through progressive stages;

**中文翻译**: II. 我们开发了一个原则性训练框架，通过渐进式阶段有效培养模型的视觉推理能力；

**解读**:  
- **原则性训练框架（principled training framework）**: 指系统化、结构化的训练方法，包括三个阶段。  
- **渐进式阶段（progressive stages）**: 指从冷启动到强化学习的逐步训练过程。

---

**英文**: III. We demonstrate state-of-the-art performance across multiple spatial reasoning benchmarks and provide insights into the development of visual reasoning abilities in LVLMs.

**中文翻译**: III. 我们在多个空间推理基准上展示了最先进的性能，并提供了关于LVLMs视觉推理能力发展的见解。

**解读**:  
- **最先进的性能（state-of-the-art performance）**: 指VILASR在空间推理任务中超越了现有模型。  
- **见解（insights）**: 指通过实验和分析得出的关于如何提升LVLMs视觉推理能力的结论。

---

### 总结

引言部分详细阐述了当前大型视觉-语言模型（LVLMs）在空间推理任务中的局限性，指出其依赖文本推理和外部感知工具的问题。受人类心理可视化的启发，作者提出了“绘图推理”范式，通过基本的绘图操作（如边界框和辅助线）实现视觉中心的空间推理，并开发了VILASR模型。采用三阶段训练框架（冷启动训练、反思性拒绝采样和强化学习），VILASR在多个空间推理任务中取得了显著提升，平均性能提高18.4%。消融研究和扩展实验进一步验证了各训练阶段的重要性，展示了模型的自我纠错和推理能力。


以下是对“2 Related Works”部分的逐句翻译和详细解读，包含中英对照，并对关键术语和背景进行解释。为了保持清晰，每句英文后附上中文翻译，并提供必要的分析。

---

### 2 Related Works

**英文**: 2.1 Reasoning in LLMs and LVLMs  
Instilling advanced reasoning capabilities within LLMs and LVLMs remains a significant challenge.

**中文翻译**:  
2.1 大型语言模型（LLMs）和大型视觉-语言模型（LVLMs）的推理  
在LLMs和LVLMs中培养高级推理能力仍然是一个重大挑战。

**解读**:  
- **高级推理能力（advanced reasoning capabilities）**: 指模型能够处理复杂逻辑问题、动态空间关系或多模态任务的能力，而不仅仅是简单的语言或视觉感知。  
- **LLMs和LVLMs**: LLMs专注于语言处理，LVLMs则结合视觉和语言处理。两者在推理能力上的提升是当前研究的热点，但面临共同的挑战，如空间推理的复杂性。

---

**英文**: Current approaches can be broadly categorized into three directions: (1) Prompt engineering: crafting prompts to elicit latent reasoning capabilities in pre-trained models [65, 80] and enable tool usage to complement model capabilities with external knowledge [1, 18] or specialized functionalities [56, 19, 60, 72].

**中文翻译**: 当前方法可以大致分为三个方向：(1) 提示工程：设计提示以激发预训练模型的潜在推理能力[65, 80]，并通过工具使用补充模型能力，引入外部知识[1, 18]或专用功能[56, 19, 60, 72]。

**解读**:  
- **提示工程（Prompt engineering）**: 指通过精心设计的输入提示（prompts）引导模型生成期望的输出，常用于挖掘预训练模型的潜在能力。  
- **潜在推理能力（latent reasoning capabilities）**: 指预训练模型中未被充分利用的推理能力，通过特定提示可以激活。  
- **工具使用（tool usage）**: 指模型调用外部工具（如搜索引擎、OCR系统）来增强其能力。  
- **外部知识（external knowledge）**: 指通过工具获取的额外信息，如数据库或网络搜索结果。  
- **专用功能（specialized functionalities）**: 指特定任务的工具，如目标检测或文本识别系统。  
- **文献引用 [65, 80], [1, 18], [56, 19, 60, 72]**: 这些引用支持提示工程在LLMs和LVLMs中的应用，以及工具使用的相关研究。

---

**英文**: These prompt-based approaches heavily depend on models’ instruction-following capabilities and often suffer from prompt sensitivity.

**中文翻译**: 这些基于提示的方法在很大程度上依赖模型的指令遵循能力，并且常常受到提示敏感性的影响。

**解读**:  
- **指令遵循能力（instruction-following capabilities）**: 指模型根据输入提示准确执行任务的能力。  
- **提示敏感性（prompt sensitivity）**: 指模型的输出对提示的措辞或格式变化非常敏感，同一任务的不同提示可能导致结果差异。  
- **局限性**: 提示工程的效果受限于模型对提示的理解能力，且难以保证一致性。

---

**英文**: (2) Supervised fine-tuning: developing tailored datasets to enhance specific reasoning capabilities [74, 66, 81] and training models to effectively utilize external tools [53, 52, 18, 8, 54, 50].

**中文翻译**: (2) 监督微调：开发定制数据集以增强特定推理能力[74, 66, 81]，并训练模型有效使用外部工具[53, 52, 18, 8, 54, 50]。

**解读**:  
- **监督微调（Supervised fine-tuning）**: 指在预训练模型上使用特定任务的数据集进行进一步训练，以提升模型在特定领域的性能。  
- **定制数据集（tailored datasets）**: 指为特定推理任务（如数学推理或空间推理）设计的高质量数据集。  
- **外部工具**: 包括目标检测、OCR等视觉工具，模型通过微调学会调用这些工具。  
- **文献引用 [74, 66, 81], [53, 52, 18, 8, 54, 50]**: 这些引用展示了监督微调在推理和工具使用中的应用。

---

**英文**: Such approaches are inherently bounded by the quality and scale of training data, limiting their potential for advanced reasoning.

**中文翻译**: 这些方法本质上受限于训练数据的质量和规模，限制了其在高级推理方面的潜力。

**解读**:  
- **训练数据的质量和规模**: 高质量、覆盖广泛的训练数据对于提升模型性能至关重要，但当前数据集在空间推理等复杂任务上的覆盖不足。  
- **高级推理的潜力（potential for advanced reasoning）**: 指处理动态、多模态或复杂逻辑任务的能力，受限于数据不足。

---

**英文**: (3) Reinforcement learning: engineering reward mechanisms to incentivize desired reasoning patterns [29, 55, 10] and optimize tool usage strategies [34].

**中文翻译**: (3) 强化学习：设计奖励机制以激励期望的推理模式[29, 55, 10]，并优化工具使用策略[34]。

**解读**:  
- **强化学习（Reinforcement learning, RL）**: 通过奖励函数引导模型优化行为，适用于培养复杂的推理模式。  
- **奖励机制（reward mechanisms）**: 指为正确推理或有效工具使用设计的奖励信号。  
- **期望的推理模式（desired reasoning patterns）**: 指逻辑清晰、连贯的推理过程。  
- **优化工具使用策略**: 指通过强化学习调整模型调用工具的方式，使其更高效。  
- **文献引用 [29, 55, 10], [34]**: 这些引用支持强化学习在推理和工具优化中的应用。

---

**英文**: While promising in textual domains, RL approaches for tool-augmented reasoning have yet to be fully investigated in multimodal scenarios.

**中文翻译**: 虽然在文本领域前景可期，但用于工具增强推理的强化学习方法在多模态场景中尚未得到充分研究。

**解读**:  
- **文本领域（textual domains）**: 指纯语言任务，如数学推理或文本生成，强化学习在此领域已有成功 Anguages: Chinese, German, Spanish, French, Italian, Japanese, Korean, Russian, Portuguese, Dutch, Swedish, Norwegian, Danish, Finnish, Polish, Czech, Hungarian, Turkish, Arabic, Hebrew

System: **中文翻译** (续):  
充分研究。

**解读** (续):  
- **工具增强推理（tool-augmented reasoning）**: 指在推理过程中结合外部工具（如OCR或目标检测）来辅助完成任务。  
- **多模态场景（multimodal scenarios）**: 指同时涉及视觉和语言输入的推理任务，如基于图像或视频的空间推理。  
- **尚未充分研究**: 表明强化学习在多模态推理中的应用仍处于早期阶段，存在研究空白。

---

**英文**: Current LVLMs either confine their reasoning to textual form [71], or rely on specialized perception tools, being constrained by tool capabilities [8, 50] and lacking reflective reasoning [54].

**中文翻译**: 当前的LVLMs要么将推理局限于文本形式[71]，要么依赖专用感知工具，受限于工具能力[8, 50]，并且缺乏反思性推理[54]。

**解读**:  
- **局限于文本形式（confine their reasoning to textual form）**: 指LVLMs将视觉信息转化为文本后进行推理，忽略了直接的视觉操作。  
- **专用感知工具（specialized perception tools）**: 指如目标检测或OCR等外部工具，这些工具的性能限制了模型的推理能力。  
- **缺乏反思性推理（lacking reflective reasoning）**: 指模型无法对推理过程或工具输出进行自我评估和修正。  
- **文献引用 [71], [8, 50], [54]**: 这些引用支持当前LVLMs的局限性描述。

---

**英文**: In contrast, we pioneer a staged training recipe that enables models to both express and reflect upon their spatial understanding through iterative drawing operations.

**中文翻译**: 相比之下，我们开创了一种分阶段训练方法，使模型能够通过迭代绘图操作表达和反思其空间理解。

**解读**:  
- **分阶段训练方法（staged training recipe）**: 指本文提出的三阶段训练框架（冷启动训练、反思性拒绝采样、强化学习）。  
- **表达和反思（express and reflect）**: 模型通过绘图操作表达空间关系，并通过反思机制检查和修正这些操作。  
- **迭代绘图操作（iterative drawing operations）**: 指在推理过程中多次绘制和调整边界框或辅助线，以逐步完善空间理解。

---

### 2.2 Visual Spatial Reasoning

**英文**: Visual spatial reasoning, as a crucial component of multimodal intelligence, extends beyond general visual perception to encompass two particularly challenging fundamental capabilities [15, 76]: relational reasoning, which involves understanding distances, directions, and spatial common sense between objects [38, 59]; and perspective transformation, which requires holding and manipulating spatial relationships [41, 69].

**中文翻译**:  
视觉空间推理作为多模态智能的关键组成部分，超越了一般的视觉感知，涵盖了两个尤其具有挑战性的基本能力[15, 76]：关系推理，涉及理解物体之间的距离、方向和空间常识[38, 59 ovided by the user, so I will continue translating and interpreting the remaining content.

System: **中文翻译** (续):  
空间常识[38, 59]；以及视角变换，需要保持和操作空间关系[41, 69]。

**解读** (续):  
- **视觉空间推理（visual spatial reasoning）**: 指基于视觉输入（如图像或视频）理解和分析物体之间的空间关系和动态变化。  
- **多模态智能（multimodal intelligence）**: 指结合多种数据类型（如视觉和语言）进行智能处理的能力。  
- **关系推理（relational reasoning）**: 指理解物体之间的空间关系，如距离、方向或相对位置（例如“物体A在物体B的左侧”）。  
- **空间常识（spatial common sense）**: 指对空间关系的直观理解，例如知道桌子通常在房间中央。  
- **视角变换（perspective transformation）**: 指在不同视角（如从正面到侧面）之间转换并保持空间关系的能力，例如判断观察者从不同角度看到的空间布局变化。  
- **文献引用 [15, 76], [38, 59], [41, 69]**: 这些引用提供了空间推理能力的理论基础和相关研究。

---

**英文**: Despite the remarkable progress of current LVLMs in basic visual tasks [24, 36, 39, 9], numerous benchmarks have revealed significant challenges in spatial reasoning [42, 27, 68, 32, 69].

**中文翻译**: 尽管当前LVLMs在基本视觉任务上取得了显著进展[24, 36, 39, 9]，但众多基准测试显示其在空间推理方面面临重大挑战[42, 27, 68, 32, 69]。

**解读**:  
- **基本视觉任务（basic visual tasks）**: 指如目标检测、图像分类或图像描述等任务，LVLMs在这些任务上表现良好。  
- **空间推理的挑战**: 指在需要精确空间关系或动态跟踪的任务中，LVLMs表现不足。  
- **基准测试（benchmarks）**: 指用于评估模型性能的标准化测试集，如迷宫导航或多视角推理任务。  
- **文献引用 [24, 36, 39, 9], [42, 27, 68, 32, 69]**: 这些引用支持LVLMs在基本视觉任务上的成功以及空间推理的困难。

---

**英文**: This limitation is partly attributed to the nature of current training datasets [22], which primarily focus on visual perception rather than spatial understanding.

**中文翻译**: 这种局限部分归因于当前训练数据集的特性[22]，这些数据集主要关注视觉感知而非空间理解。

**解读**:  
- **训练数据集的特性（nature of current training datasets）**: 指现有数据集（如图像描述数据集）更注重物体识别或语义理解，而缺乏针对空间推理的专门数据。  
- **视觉感知（visual perception）**: 指识别图像中的物体或场景内容。  
- **空间理解（spatial understanding）**: 指理解物体之间的空间关系和动态变化。  
- **文献引用 [22]**: 支持数据集局限性的观点。

---

**英文**: Recent works have attempted to address this challenge through various approaches.

**中文翻译**: 近期研究尝试通过各种方法解决这一挑战。

**解读**:  
- **各种方法（various approaches）**: 指近期针对空间推理提出的解决方案，接下来会具体介绍。

---

**英文**: For image-based spatial reasoning, several studies have proposed synthetic datasets [38, 5, 7, 4].

**中文翻译**: 对于基于图像的空间推理，一些研究提出了合成数据集[38, 5, 7, 4]。

**解读**:  
- **基于图像的空间推理（image-based spatial reasoning）**: 指基于静态图像的空间关系分析。  
- **合成数据集（synthetic datasets）**: 指人工生成的数据集，专门设计用于训练空间推理能力，例如包含标注的空间关系数据。  
- **文献引用 [38, 5, 7, 4]**: 这些引用展示了针对图像空间推理的合成数据集研究。

---

**英文**: For video-based spatial reasoning, approaches have emerged either by incorporating 3D representations as bridging knowledge [82] or by tracking objects across frames [37].

**中文翻译**: 对于基于视频的空间推理，出现了一些方法，要么通过引入3D表示作为桥梁知识[82]，要么通过跨帧跟踪物体[37]。

**解读**:  
- **基于视频的空间推理（video-based spatial reasoning）**: 指基于视频序列的空间关系分析，涉及物体在时间维度上的动态变化。  
- **3D表示（3D representations）**: 指使用三维模型来表示物体的空间结构，作为推理的辅助信息。  
- **跨帧跟踪（tracking objects across frames）**: 指在视频的连续帧中跟踪物体的位置和运动轨迹。  
- **文献引用 [82], [37]**: 支持视频空间推理的两种主要方法。

---

**英文**: However, systematic approaches to enhance LVLMs’ spatial reasoning capabilities that can generalize across both images and videos remain largely unexplored.

**中文翻译**: 然而，能够同时泛化到图像和视频的、增强LVLMs空间推理能力的系统性方法仍未得到充分探索。

**解读**:  
- **系统性方法（systematic approaches）**: 指全面、结构化的方法，能够统一处理图像和视频的空间推理任务。  
- **泛化到图像和视频（generalize across both images and videos）**: 指模型能力应适用于静态图像和动态视频的多种场景。  
- **未充分探索**: 表明在跨模态空间推理的系统性方法上存在研究空白。

---

**英文**: Our work fills this gap by developing a principled reasoning framework in LVLMs.

**中文翻译**: 我们的工作通过在LVLMs中开发一个原则性推理框架填补了这一空白。

**解读**:  
- **原则性推理框架（principled reasoning framework）**: 指本文提出的三阶段训练框架，系统性地提升LVLMs的空间推理能力。  
- **填补空白**: 表明本文的工作在跨图像和视频的空间推理方面提出了创新性解决方案。

---

### 总结

“相关工作”部分回顾了在LLMs和LVLMs中培养推理能力的现有方法，包括提示工程、监督微调和强化学习三种主要方向，指出这些方法在多模态空间推理中的局限性，如对外部工具的依赖、提示敏感性、数据集质量不足以及缺乏反思性推理。视觉空间推理是多模态智能的核心，涉及关系推理和视角变换两大挑战，但当前LVLMs由于训练数据集的局限，在空间推理方面表现不足。尽管近期研究尝试通过合成数据集或3D表示等方法改进图像和视频的空间推理，但能够同时泛化到两者上的系统性方法仍未充分探索。本文的工作通过提出“绘图推理”范式和三阶段训练框架，填补了这一研究空白，为提升LVLMs的空间推理能力提供了新的方向。


以下是对“3 Methodology”部分的逐句翻译和详细解读，包含中英对照，并对关键术语、方法和背景进行解释。为了保持清晰，每句英文后附上中文翻译，并提供必要的分析。文中涉及的公式和图表也会在翻译后进行说明。

---

### 3 Methodology

**英文**: In this section, we present our approach to advancing spatial reasoning capabilities in LVLMs.

**中文翻译**: 在本节中，我们介绍了提升大型视觉-语言模型（LVLMs）空间推理能力的方法。

**解读**:  
- **空间推理能力（spatial reasoning capabilities）**: 指LVLMs理解和分析物体间空间关系及动态变化的能力，例如在图像或视频中判断物体位置或轨迹。  
- **LVLMs**: 大型视觉-语言模型，能够处理视觉和语言输入，目标是增强其在空间推理任务中的表现。

---

**英文**: Given a spatial reasoning question Q and a visual input I = {In}N n=1, where each In represents a single image, N = 1 corresponds to a single image input, and N > 1 denotes a video sequence or multiple image inputs, our goal is to enable LVLMs to derive the answer A through iterative visual drawing and thinking.

**中文翻译**: 给定一个空间推理问题 Q 和视觉输入 I = {In}N n=1，其中每个 In 代表单张图像，N = 1 对应单张图像输入，N > 1 表示视频序列或多张图像输入，我们的目标是使LVLMs通过迭代的视觉绘图和思考推导出答案 A。

**解读**:  
- **空间推理问题 Q**: 指要求模型分析空间关系的提问，例如“椅子左边是什么物体？”或“视频中桌子的数量是多少？”。  
- **视觉输入 I = {In}N n=1**: 表示输入可以是单张图像（N=1）或多张图像/视频帧（N>1）。  
- **迭代的视觉绘图和思考（iterative visual drawing and thinking）**: 指模型通过多次绘制边界框或辅助线并结合自然语言推理，逐步解决问题。  
- **答案 A**: 指最终的推理结果，可能为多选题选项或数值答案。

---

**英文**: We first introduce our reasoning paradigm (3.1), and then detail the training framework (3.2) that cultivates this reasoning capability.

**中文翻译**: 我们首先介绍我们的推理范式（3.1节），然后详细描述培养这种推理能力的训练框架（3.2节）。

**解读**:  
- **推理范式（reasoning paradigm）**: 指“在空间中通过绘图进行推理”的方法，具体在3.1节阐述。  
- **训练框架（training framework）**: 指三阶段训练方法（冷启动训练、反思性拒绝采样、强化学习），在3.2节详细说明。

---

### 3.1 Drawing to Reason in Space

**英文**: We propose “drawing to reason in space,” a reasoning paradigm that empowers LVLMs to decompose complex spatial reasoning tasks into a sequence of interpretable visual drawing and thinking steps, as illustrated in Figure 1.

**中文翻译**: 我们提出“在空间中通过绘图进行推理”，这一推理范式使LVLMs能够将复杂空间推理任务分解为一系列可解释的视觉绘图和思考步骤，如图1所示。

**解读**:  
- **绘图推理（drawing to reason in space）**: 通过绘制边界框和辅助线等操作，直接在视觉空间中表达和分析空间关系。  
- **分解复杂任务（decompose complex spatial reasoning tasks）**: 指将复杂问题拆分为多个简单步骤，例如先标记物体位置，再分析关系。  
- **可解释的（interpretable）**: 指绘图和推理步骤清晰，易于理解模型的推理过程。  
- **图1（Figure 1）**: 展示了绘图推理的具体示例，可能是分解步骤的视觉化表示。

---

**英文**: Formally, given the visual input I and question Q, the LVLM M generates a multi-step reasoning path R to derive the final answer.

**中文翻译**: 形式上，给定视觉输入 I 和问题 Q，LVLM M 生成多步骤推理路径 R 以推导出最终答案。

**解读**:  
- **LVLM M**: 指大型视觉-语言模型，即本文的VILASR模型。  
- **多步骤推理路径 R**: 指推理过程由多个步骤组成，每个步骤包括思考和绘图操作。

---

**英文**: The reasoning path R can be represented as a T-step chain: R = {(rt, et, ot)}T t=1, where each step interleaves natural language reasoning rt, drawing operations et, and observed results ot from executing the drawing operations [73].

**中文翻译**: 推理路径 R 可以表示为一个 T 步链：R = {(rt, et, ot)}T t=1，其中每个步骤交织自然语言推理 rt、绘图操作 et 和执行绘图操作后观察到的结果 ot [73]。

**解读**:  
- **T 步链（T-step chain）**: 指推理过程分为 T 个步骤，每个步骤包含三部分：  
  - **自然语言推理 rt**: 模型的文本推理内容，例如描述当前分析或计划。  
  - **绘图操作 et**: 模型执行的视觉操作，如绘制边界框或辅助线。  
  - **观察结果 ot**: 绘图操作后生成的带标注的图像。  
- **交织（interleaves）**: 指推理和绘图操作在每一步中协同进行，相互促进。  
- **文献引用 [73]**: 支持推理路径的结构化表示方法。

---

**英文**: This iterative process continues until M reaches a conclusive answer in the final reasoning step rT.

**中文翻译**: 这一迭代过程持续进行，直到 M 在最终推理步骤 rT 中得出结论性答案。

**解读**:  
- **迭代过程（iterative process）**: 指模型通过多次推理和绘图逐步逼近答案。  
- **结论性答案（conclusive answer）**: 指最终确定的答案，通常在最后一步 rT 中生成。

---

**英文**: Next, we elaborate on the core components of the paradigm.

**中文翻译**: 接下来，我们详细阐述该范式的核心组成部分。

**解读**: 指以下内容将介绍绘图操作和每步推理的具体机制。

---

**英文**: Drawing operations for spatial reasoning. We equip LVLMs with two essential drawing operations T = {Tbox, Tline} for bounding box annotation and auxiliary line drawing, respectively.

**中文翻译**: 空间推理的绘图操作。我们为LVLMs配备了两种基本绘图操作 T = {Tbox, Tline}，分别用于边界框标注和辅助线绘制。

**解读**:  
- **绘图操作（drawing operations）**: 指模型在图像上执行的视觉操作，用于表达空间关系。  
- **T = {Tbox, Tline}**: 表示两种操作：  
  - **Tbox**: 绘制边界框，用于标记物体位置。  
  - **Tline**: 绘制辅助线，用于表示物体间的空间关系或轨迹。  
- **基本（essential）**: 强调这两种操作简单但足以支持空间推理。

---

**英文**: These operations are fundamental to spatial reasoning as they enable explicit representation of object locations and their spatial transitions—bounding boxes anchor object positions while auxiliary lines visualize spatial trajectories and relationships.

**中文翻译**: 这些操作对空间推理至关重要，因为它们能够明确表示物体位置及其空间转换——边界框固定物体位置，而辅助线可视化空间轨迹和关系。

**解读**:  
- **明确表示（explicit representation）**: 指通过可视化操作直观表达空间信息，而非依赖文本描述。  
- **物体位置（object locations）**: 指物体在图像中的具体坐标。  
- **空间转换（spatial transitions）**: 指物体在空间中的移动或视角变化。  
- **空间轨迹和关系（spatial trajectories and relationships）**: 指物体运动路径或物体间的方向、距离等关系。

---

**英文**: Each operation τ ∈ T accepts three parameters:  
• k: the index of the target image from either the original input I or previous drawing outputs {oi};  
• p: single or multiple spatial coordinates for annotating bounding boxes or drawing auxiliary lines;  
• l: semantic labels describing the annotated content.

**中文翻译**: 每个操作 τ ∈ T 接受三个参数：  
• k：目标图像的索引，来自原始输入 I 或之前的绘图输出 {oi}；  
• p：用于标注边界框或绘制辅助线的单个或多个空间坐标；  
• l：描述标注内容的语义标签。

**解读**:  
- **操作 τ**: 指 Tbox 或 Tline。  
- **参数 k**: 指定操作的目标图像，可以是原始图像或之前绘图生成的图像。  
- **参数 p**: 空间坐标，例如边界框的四个顶点坐标或辅助线的起点和终点。  
- **参数 l**: 语义标签，例如“椅子”或“左边界”，用于描述绘图内容的含义。

---

**英文**: The execution output of each drawing operation is an annotated version of the target image, preserving the original content while overlaying the specified visual elements.

**中文翻译**: 每个绘图操作的执行输出是目标图像的标注版本，保留原始内容，同时叠加指定的视觉元素。

**解读**:  
- **标注版本（annotated version）**: 指在原始图像上添加边界框或辅助线后的新图像。  
- **保留原始内容（preserving the original content）**: 确保绘图操作不破坏原始图像信息。  
- **指定的视觉元素（specified visual elements）**: 指边界框或辅助线等标注。

---

**英文**: While this minimal operation set proves effective for spatial reasoning, it can be readily extended with additional visual manipulation tools in future work.

**中文翻译**: 虽然这一最小操作集在空间推理中被证明是有效的，但未来可以轻松扩展到包括额外的视觉操作工具。

**解读**:  
- **最小操作集（minimal operation set）**: 指当前仅使用边界框和辅助线两种操作，简单但有效。  
- **扩展（extended）**: 未来可加入更多操作，如缩放或裁剪，以处理更复杂的任务。

---

**英文**: Per-step spatial reasoning. At the t-th reasoning step, M generates both natural language reasoning rt and drawing operations et based on the entire interaction history:  
rt, et = {ej t = (kj t , pj t , lj t )}mt j=1 = M(I, Q, R<t), (1)

**中文翻译**: 每步空间推理。在第 t 个推理步骤中，M 基于整个交互历史生成自然语言推理 rt 和绘图操作 et：  
rt, et = {ej t = (kj t , pj t , lj t )}mt j=1 = M(I, Q, R<t), (1)

**解读**:  
- **每步空间推理（per-step spatial reasoning）**: 指推理过程中的单个步骤，结合文本推理和绘图操作。  
- **交互历史（interaction history）**: 指之前的推理路径 R<t = {(ri, ei, oi)}i<t，包含所有之前的推理、操作和输出。  
- **公式 (1)**: 表示模型 M 根据输入 I、问题 Q 和历史 R<t 生成当前步骤的 rt（文本推理）和 et（绘图操作）。  
- **et = {ej t = (kj t , pj t , lj t )}mt j=1**: 表示第 t 步的绘图操作包含 mt 个子操作，每个子操作由目标图像索引 kj、坐标 pj 和标签 lj 组成。

---

**英文**: where et specifies a set of mt operations to be executed, ej t denote each single operation with three necessary parameters, and R<t = {(ri, ei, oi)}i<t means the reasoning history before step t.

**中文翻译**: 其中 et 指定一组要执行的 mt 个操作，ej t 表示每个单独操作，包含三个必要参数，R<t = {(ri, ei, oi)}i<t 表示第 t 步之前的推理历史。

**解读**:  
- **mt 个操作**: 指第 t 步可能包含多个绘图操作（如多个边界框或辅助线）。  
- **三个必要参数**: 即 k（图像索引）、p（坐标）、l（标签）。  
- **推理历史 R<t**: 包含之前所有步骤的推理（ri）、操作（ei）和输出（oi）。

---

**英文**: The operations in et can target different images through distinct indices kj t, which is crucial for both image and video reasoning as key information may come from multiple previous drawing outputs or different video frames.

**中文翻译**: et 中的操作可以通过不同的索引 kj t 针对不同图像，这对于图像和视频推理都至关重要，因为关键信息可能来自多个之前的绘图输出或不同的视频帧。

**解读**:  
- **不同图像（different images）**: 指操作可以针对原始输入图像或之前生成的标注图像。  
- **关键信息（key information）**: 指推理所需的空间关系，可能分布在多张图像或视频帧中。  
- **图像和视频推理**: 强调方法适用于静态图像和动态视频。

---

**英文**: After execution, these operations output a set of annotated images ot = {oj t }mt j=1, which are sequentially indexed to maintain order.

**中文翻译**: 执行后，这些操作输出一组标注图像 ot = {oj t }mt j=1，这些图像按顺序索引以保持顺序。

**解读**:  
- **标注图像 ot**: 指第 t 步绘图操作生成的带边界框或辅助线的图像集合。  
- **按顺序索引（sequentially indexed）**: 确保生成的图像有明确的编号，便于后续引用。

---

**英文**: To enable index-based image retrieval for drawing, M has access to the indices of all available images, including both the original visual input and operation-generated outputs.

**中文翻译**: 为了支持基于索引的图像检索以进行绘图，M 可以访问所有可用图像的索引，包括原始视觉输入和操作生成的输出。

**解读**:  
- **基于索引的图像检索（index-based image retrieval）**: 指模型通过图像索引（如 k）选择操作目标图像。  
- **所有可用图像**: 包括原始输入 I 和之前绘图生成的图像 {oi}。

---

**英文**: The process terminates when rt reaches a final answer, in which case et = ∅ and ot = ∅.

**中文翻译**: 当 rt 达到最终答案时，推理过程终止，此时 et = ∅ 且 ot = ∅。

**解读**:  
- **最终答案（final answer）**: 指推理过程得出结论，问题得到解决。  
- **et = ∅, ot = ∅**: 表示最后一步无需进一步绘图操作，也无新图像输出。

---

**英文**: [Footnote 2] Since this work focuses on inter-object spatial relationships rather than object-specific details, we adopt only basic drawing operations rather than common visual manipulations like zooming or cropping [8, 46].

**中文翻译**: [脚注 2] 由于本工作关注物体之间的空间关系而非物体特定细节，我们仅采用基本绘图操作，而非常见的视觉操作如缩放或裁剪[8, 46]。

**解读**:  
- **物体之间的空间关系（inter-object spatial relationships）**: 指如距离、方向等关系，而非物体的纹理或颜色等细节。  
- **基本绘图操作（basic drawing operations）**: 指边界框和辅助线，简单但足以anguardia: 足以处理空间推理任务。  
- **常见的视觉操作（zooming or cropping）**: 指如缩放或裁剪等操作，因与空间推理无关而未采用。  
- **文献引用 [8, 46]**: 指出其他研究中使用的复杂视觉操作。

---

### 3.2 Training Framework

**英文**: Our training framework consists of three stages: cold-start training with synthetic offline data to establish basic visual interaction capabilities, reflective rejection sampling to cultivate reflection behaviors, and reinforcement learning for incentivizing reasoning potentials, as illustrated in Figure 2.

**中文翻译**: 我们的训练框架包括三个阶段：使用合成离线数据进行冷启动训练以建立基本视觉交互能力，反思性拒绝采样以培养反思行为，以及强化学习以激励推理潜力，如图2所示。

**解读**:  
- **三阶段训练框架**:  
  1. **冷启动训练（cold-start training）**: 使用合成数据初始化绘图能力。  
  2. **反思性拒绝采样（reflective rejection sampling）**: 增强模型的自我纠错能力。  
  3. **强化学习（reinforcement learning）**: 优化推理过程和答案准确性。  
- **图2（Figure 2）**: 展示了三阶段训练的流程图。  
- **视觉交互能力（visual interaction capabilities）**: 指模型与图像交互的能力，如绘制边界框或辅助线。  
- **反思行为（reflection behaviors）**: 指模型检查和修正推理过程的能力。  
- **推理潜力（reasoning potentials）**: 指模型在复杂推理任务中的潜在能力。

---

**英文**: During training, we focus on multiple-choice questions (e.g., “Which object is to the left of the chair? A. table ...”) and numerical questions (e.g., “How many tables appear in this video?”) due to their amenability to automated correctness evaluation, strategically excluding free-form answer questions (e.g., describing motion trajectories).

**中文翻译**: 在训练过程中，我们专注于多选题（例如“椅子左边是什么物体？A. 桌子……”）和数值问题（例如“视频中出现了多少张桌子？”），因为它们易于自动正确性评估，战略性地排除了自由形式答案问题（例如描述运动轨迹）。

**解读**:  
- **多选题和数值问题**: 这类问题答案明确，易于通过规则自动评估正确性。  
- **自由形式答案问题（free-form answer questions）**: 指开放性问题，如描述轨迹，难以自动评估。  
- **战略性排除**: 为了简化训练和评估，专注于结构化问题。

---

**英文**: In what follows, we first present our reward function design that guides all three stages, followed by detailed descriptions of the stage-wise training procedures.

**中文翻译**: 接下来，我们首先介绍指导所有三个阶段的奖励函数设计，然后详细描述分阶段训练过程。

**解读**:  
- **奖励函数（reward function）**: 强化学习和训练过程中的关键部分，用于评估模型表现。  
- **分阶段训练过程（stage-wise training procedures）**: 指冷启动、反思性拒绝采样和强化学习的具体实现。

---

**英文**: Reward function. For reward design, we propose a rule-based function that combines answer correctness and reasoning format adherence:  
S = 1(Scorrect > β) · (Scorrect(A, ˆA) + Sformat(R)), (2)

**中文翻译**: 奖励函数。对于奖励设计，我们提出了一个基于规则的函数，结合答案正确性和推理格式遵循：  
S = 1(Scorrect > β) · (Scorrect(A, ˆA) + Sformat(R)), (2)

**解读**:  
- **奖励函数 S**: 综合评估答案正确性（Scorrect）和推理格式（Sformat）。  
- **Scorrect(A, ˆA)**: 评估预测答案 ˆA 与真实答案 A 的匹配程度。  
- **Sformat(R)**: 评估推理路径 R 的结构有效性，例如操作是否可执行。  
- **β**: 阈值，确保只有当答案正确性达到一定水平时才考虑格式奖励，防止模型只优化格式而忽略准确性。  
- **公式 (2)**: 表示奖励是正确性和格式分数的加权组合，仅当 Scorrect > β 时生效。

---

**英文**: where β is a threshold that ensures format rewards are only granted when a minimum correctness threshold is met, preventing reward hacking where the model might optimize for format adherence at the expense of task accuracy.

**中文翻译**: 其中 β 是一个阈值，确保只有当答案正确性达到最低阈值时才授予格式奖励，防止模型为了格式遵循而牺牲任务准确性的奖励欺骗行为。

**解读**:  
- **奖励欺骗（reward hacking）**: 指模型优化次要目标（如格式）而忽略主要目标（正确性）。  
- **最低正确性阈值（minimum correctness threshold）**: 确保模型优先保证答案准确性。

---

**英文**: ˆA is the predicted answer that we extract from the model’s final reasoning step rT using rule-based parsing.

**中文翻译**: ˆA 是我们通过基于规则的解析从模型的最终推理步骤 rT 中提取的预测答案。

**解读**:  
- **预测答案 ˆA**: 模型在最后一步 rT 中生成的答案。  
- **基于规则的解析（rule-based parsing）**: 使用预定义规则从文本推理中提取答案，例如识别多选题的选项或数值。

---

**英文**: Specifically, we compute Scorrect as follows:  
Scorrect(A, ˆA) =  
(1(A = ˆA), for multiple-choice questions,  
1/|C| ∑θ∈C 1(|A− ˆA|/A < 1 − θ), for numerical questions. (3)

**中文翻译**: 具体而言，我们按以下方式计算 Scorrect：  
Scorrect(A, ˆA) =  
(1(A = ˆA)，对于多选题，  
1/|C| ∑θ∈C 1(|A− ˆA|/A < 1 − θ)，对于数值问题。(3)

**解读**:  
- **Scorrect 的计算方法**:  
  - **多选题**: 如果预测答案 ˆA 与真实答案 A 完全匹配，Scorrect = 1，否则为 0。  
  - **数值问题**: 使用平均相对精度（Mean Relative Accuracy, MRA），评估预测值与真实值的相对误差是否低于多个置信度阈值（C = {0.50, 0.55, ..., 0.95}）。  
- **公式 (3)**: 定义了正确性分数的计算规则，数值问题的评分更复杂，考虑多个误差阈值。  
- **平均相对精度（MRA）**: 一种鲁棒的评估方法，衡量预测值在不同误差容忍度下的准确性。

---

**英文**: For multiple-choice questions, we simply check the exact match between the predicted and ground-truth answers.

**中文翻译**: 对于多选题，我们简单检查预测答案与真实答案的完全匹配。

**解读**:  
- **完全匹配（exact match）**: 多选题的评分方法简单，答案完全一致得 1 分，否则得 0 分。  
- **真实答案（ground-truth answers）**: 指数据集提供的标准答案。

---

**英文**: For numerical questions, we adopt Mean Relative Accuracy (MRA) [69] for reward computation, which provides a more robust evaluation than conventional metrics like absolute error or fixed thresholding.

**中文翻译**: 对于数值问题，我们采用平均相对精度（MRA）[69]进行奖励计算，这比传统指标（如绝对误差或固定阈值）提供了更鲁棒的评估。

**解读**:  
- **平均相对精度（MRA）**: 通过检查预测值与真实值的相对误差是否低于多个阈值，综合评估模型的精度。  
- **鲁棒的评估（robust evaluation）**: MRA 考虑多个置信度水平，比单一误差指标更全面。  
- **文献引用 [69]**: 指 MRA 方法的出处。

---

**英文**: Instead, MRA examines the prediction accuracy across multiple confidence levels C = {0.50, 0.55, . . . , 0.95}.

**中文翻译**: MRA 检查多个置信度水平 C = {0.50, 0.55, ..., 0.95} 下的预测准确性。

**解读**:  
- **置信度水平 C**: 一组预定义的误差阈值，用于评估预测值的相对误差是否满足不同严格程度的要求。  
- **预测准确性（prediction accuracy）**: 指预测值与真实值的接近程度。

---

**英文**: For each threshold θ ∈ C, it checks if the relative error between predicted value A and ground truth ˆA falls below (1 − θ).

**中文翻译**: 对于每个阈值 θ ∈ C，检查预测值 A 和真实值 ˆA 之间的相对误差是否低于 (1 − θ)。

**解读**:  
- **相对误差（relative error）**: 定义为 |A − ˆA|/A，表示预测值与真实值的偏差比例。  
- **1 − θ**: 误差容忍度，例如当 θ = 0.95 时，相对误差需小于 5%。

---

**英文**: The final score averages these binary outcomes, effectively measuring the model’s precision across different stringency levels.

**中文翻译**: 最终分数平均这些二值结果，有效测量模型在不同严格程度下的精度。

**解读**:  
- **二值结果（binary outcomes）**: 指每个阈值 θ 下的误差是否满足条件的 0 或 1 分。  
- **不同严格程度（different stringency levels）**: 指多个误差阈值，反映模型在不同精度要求下的表现。

---

**英文**: For Sformat, we evaluate the quality of reasoning format based on the structural validity of R, assigning a score of 1 if all operations in the reasoning path R are executable, and 0 otherwise.

**中文翻译**: 对于 Sformat，我们基于推理路径 R 的结构有效性评估推理格式的质量，如果 R 中的所有操作都可执行，则得 1 分，否则得 0 分。

**解读**:  
- **推理格式的质量（quality of reasoning format）**: 指推理路径是否逻辑清晰、操作可执行。  
- **结构有效性（structural validity）**: 指推理路径 R 中的操作是否符合格式要求，例如绘图操作的参数是否正确。  
- **可执行（executable）**: 指操作能够实际在图像上实现，如绘制有效的边界框或辅助线。

---

**英文**: Cold-start training. Prompting alone often fails to elicit effective visual manipulation abilities in LVLMs for reasoning [19, 8].

**中文翻译**: 冷启动训练。仅靠提示往往无法激发LVLMs有效的视觉操作能力用于推理[19, 8]。

**解读**:  
- **冷启动训练（cold-start training）**: 指在模型能力较弱时，使用合成数据初始化训练。  
- **视觉操作能力（visual manipulation abilities）**: 指如绘制边界框或辅助线的能力。  
- **文献引用 [19, 8]**: 指出提示工程在激发视觉推理能力上的不足。

---

**英文**: Therefore, we initialize models’ ability to reason in space with drawing operations through supervised learning on a synthetic dataset Dcold.

**中文翻译**: 因此，我们通过在合成数据集 Dcold 上进行监督学习，初始化模型的空间推理能力与绘图操作。

**解读**:  
- **监督学习（supervised learning）**: 使用标注数据训练模型，使其学会生成推理路径和绘图操作。  
- **合成数据集 Dcold**: 指人工生成的数据集，包含视觉输入、问题和推理路径。

---

**英文**: The training objective is to minimize the average negative log-likelihood over all reasoning and operation tokens:  
Lcold = E(I,Q,A,R={(rt,et,ot)}T t=1)∼Dcold [−1/N ∑T t=1 log p(rt, et|I, Q, R<t)] (4)

**中文翻译**: 训练目标是最小化所有推理和操作标记的平均负对数似然：  
Lcold = E(I,Q,A,R={(rt,et,ot)}T t=1)∼Dcold [−1/N ∑T t=1 log p(rt, et|I, Q, R<t)] (4)

**解读**:  
- **负对数似然（negative log-likelihood）**: 监督学习的常见损失函数，用于衡量模型生成正确推理路径的概率。  
- **N = ∑T t=1(|rt| + |et|)**: 表示推理路径中所有推理和操作标记的总数量。  
- **公式 (4)**: 定义了冷启动训练的损失函数，目标是最大化推理和操作的生成概率。  
- **数据集 Dcold**: 提供训练所需的输入、问题、答案和推理路径。

---

**英文**: where N = PT t=1(|rt| + |et|) denotes the total number of tokens in reasoning steps and drawing operations.

**中文翻译**: 其中 N = ∑T t=1(|rt| + |et|) 表示推理步骤和绘图操作中的标记总数。

**解读**:  
- **标记总数（total number of tokens）**: 指推理文本（rt）和绘图操作（et）中的所有标记（例如单词或操作参数）。  
- **|rt|, |et|**: 分别表示第 t 步推理文本和绘图操作的标记数量。

---

**英文**: To construct Dcold, we first collect a diverse set of image and video question-answering pairs from publicly available datasets, comprising visual inputs I, questions Q, and ground-truth answers A.

**中文翻译**: 为了构建 Dcold，我们首先从公开数据集收集多样化的图像和视频问答对，包括视觉输入 I、问题 Q 和真实答案 A。

**解读**:  
- **公开数据集（publicly available datasets）**: 指如视觉问答（VQA）或视频问答数据集。  
- **问答对（question-answering pairs）**: 包含问题、输入和答案的配对数据，用于训练。

---

**英文**: We then leverage Qwen2.5-72B-VL [2] to generate reasoning paths following our reasoning paradigm described in §3.1.

**中文翻译**: 然后我们利用 Qwen2.5-72B-VL [2] 生成遵循我们在 3.1 节描述的推理范式的推理路径。

**解读**:  
- **Qwen2.5-72B-VL [2]**: 一种强大的视觉-语言模型，用于生成高质量的推理路径。  
- **推理路径（reasoning paths）**: 指包含推理步骤和绘图操作的序列，遵循绘图推理范式。

---

**英文**: The generated paths are subsequently filtered based on rule-based correctness and format checking in Eq. 2 to ensure high-quality demonstrations of spatial reasoning.

**中文翻译**: 生成的推理路径随后根据公式 (2) 中的基于规则的正确性和格式检查进行过滤，以确保高质量的空间推理演示。

**解读**:  
- **基于规则的正确性和格式检查**: 使用公式 (2) 的奖励函数评估推理路径的答案正确性和格式有效性。  
- **高质量演示（high-quality demonstrations）**: 指经过筛选的推理路径，能够作为训练的优秀示例。

---

**英文**: Appendix B shows more details.

**中文翻译**: 附录 B 显示更多细节。

**解读**:  
- **附录 B**: 提供数据集构建和过滤的具体细节，可能包括数据集规模、生成方法等。

---

**英文**: Reflective rejection sampling. The success of RL often relies on the model’s initial capability to exhibit reflective behaviors [14].

**中文翻译**: 反思性拒绝采样。强化学习的成功往往依赖于模型最初展现反思行为的能力[14]。

**解读**:  
- **反思行为（reflective behaviors）**: 指模型在推理过程中检查和修正自身操作的能力。  
- **强化学习（RL）**: 需要模型具备一定的基础能力，反思行为是 RL 优化的前提。  
- **文献引用 [14]**: 支持反思行为对强化学习的重要性。

---

**英文**: In our case, the ability to reflect on and revise drawing operations based on observed execution output is crucial.

**中文翻译**: 在我们的情况下，基于观察到的执行输出反思和修正绘图操作的能力至关重要。

**解读**:  
- **反思和修正（reflect on and revise）**: 指模型根据绘图结果（ot）调整后续操作（et）。  
- **执行输出（execution output）**: 指绘图操作生成的标注图像。

---

**英文**: Accordingly, we define reflective behavior as the recurrence of identical labels across different time steps within the same reasoning process.

**中文翻译**: 因此，我们将反思行为定义为在同一推理过程中不同时间步骤中相同标签的重复出现。

**解读**:  
- **相同标签的重复（recurrence of identical labels）**: 指在不同步骤中对同一物体（如“椅子”）进行多次标注，通常表示模型在检查和修正之前的标注。

---

**英文**: Formally, for a reasoning path R, reflection occurs when:  
∃(t1, t2, u, v) : (lu t1 = lv t2) ∧ (eu t1 ≠ ev t2) in R = {(rt, et = {ej t = (kj t , pj t , lj t )}mt j=1, ot)}T t=1, (5)

**中文翻译**: 形式上，对于推理路径 R，当以下条件满足时发生反思：  
∃(t1, t2, u, v) : (lu t1 = lv t2) ∧ (eu t1 ≠ ev t2) 在 R = {(rt, et = {ej t = (kj t , pj t , lj t )}mt j=1, ot)}T t=1 中，(5)

**解读**:  
- **反思的定义（公式 5）**: 如果在不同步骤 t1 和 t2 中，语义标签 lu t1 和 lv t2 相同（例如都是“椅子”），但绘图操作 eu t1 和 ev t2 不同（例如不同的边界框坐标），则表示模型在反思并修正操作。  
- **推理路径 R**: 包含所有步骤的推理、操作和输出。

---

**英文**: where li t1 and lj t2 represent semantic labels assigned to drawing operations at different reasoning steps, and ej t denote the parameters of one drawing operation.

**中文翻译**: 其中 li t1 和 lj t2 表示不同推理步骤中分配给绘图操作的语义标签，ej t 表示一个绘图操作的参数。

**解读**:  
- **语义标签（semantic labels）**: 如“椅子”或“桌子”，用于描述绘图内容。  
- **绘图操作参数（parameters of one drawing operation）**: 包括图像索引 k、坐标 p 和标签 l。

---

**英文**: However, after cold-start training, we observe that the resulting model, denoted as Mcold, infrequently exhibits such reflective behavior (see §4.3 for more details), potentially limiting the effectiveness of subsequent RL optimization.

**中文翻译**: 然而，冷启动训练后，我们观察到所得模型 Mcold 很少展现这种反思行为（详见 4.3 节），可能限制后续强化学习优化的效果。

**解读**:  
- **Mcold**: 冷启动训练后的模型。  
- **反思行为不足**: 表明冷启动训练的模型缺乏自我纠错能力。  
- **4.3 节**: 可能包含实验数据，说明反思行为的频率较低。

---

**英文**: To address this limitation, we introduce a novel reflective rejection sampling mechanism.

**中文翻译**: 为了解决这一局限性，我们引入了一种新颖的反思性拒绝采样机制。

**解读**:  
- **反思性拒绝采样（reflective rejection sampling）**: 一种选择性训练方法，筛选具有正确答案、正确格式和反思行为的推理路径。

---

**英文**: Given a batch of spatial reasoning examples Dreflect, we first use Mcold to sample corresponding reasoning paths, and then continue fine-tune Mcold with the following objective:  
Lreflect = E(I,Q,A)∼Dreflect,R∼Mcold(·|I,Q) [−1/N ∑T t=1 log p(rt, et|I, Q, R<t)]φ, (6)

**中文翻译**: 给定一批空间推理示例 Dreflect，我们首先使用 Mcold 采样相应的推理路径，然后继续以以下目标微调 Mcold：  
Lreflect = E(I,Q,A)∼Dreflect,R∼Mcold(·|I,Q) [−1/N ∑T t=1 log p(rt, et|I, Q, R<t)]φ, (6)

**解读**:  
- **Dreflect**: 用于反思性拒绝采样的数据集，包含空间推理示例。  
- **采样推理路径（sample corresponding reasoning paths）**: 使用 Mcold 生成推理路径 R。  
- **微调目标（Lreflect）**: 最小化负对数似然，仅对满足 φ 条件的路径进行训练。  
- **φ**: 二值过滤器，仅当推理路径满足正确性、格式和反思条件时，φ = 1。  
- **公式 (6)**: 定义了反思性拒绝采样的训练目标。

---

**英文**: where φ acts as a binary filter that equals 1 if and only if the reasoning path R not only yields the correct answer A and meets format criteria, but also satisfies the reflection condition in Eq. 5.

**中文翻译**: 其中 φ 是一个二值过滤器，仅当推理路径 R 产生正确答案 A、满足格式标准且满足公式 (5) 的反思条件时，φ = 1。

**解读**:  
- **二值过滤器（binary filter）**: 确保只训练高质量的推理路径。  
- **正确答案、格式、反思条件**: 推理路径需同时满足三者才会被用于训练。

---

**英文**: This selective training strategy encourages the model to learn from high-quality reasoning paths that demonstrate both reflective thinking and correct reasoning, facilitating the development of self-correction capabilities crucial for subsequent RL optimization.

**中文翻译**: 这种选择性训练策略鼓励模型学习高质量的推理路径，这些路径展示反思性思考和正确推理，促进自我纠错能力的发展，这对后续强化学习优化至关重要。

**解读**:  
- **高质量推理路径（high-quality reasoning paths）**: 指同时具有正确性、格式规范和反思行为的路径。  
- **自我纠错能力（self-correction capabilities）**: 指模型在推理中修正错误的能力。  
- **强化学习优化（RL optimization）**: 指下一阶段的训练目标。

---

**英文**: Reinforcement learning. We further optimize the model using RL with carefully designed rollout policies.

**中文翻译**: 强化学习。我们使用精心设计的滚动策略进一步优化模型。

**解读**:  
- **滚动策略（rollout policies）**: 强化学习中生成推理路径的策略，需避免无效或循环推理。

---

**英文**: During policy rollout, we monitor the reasoning process and apply early termination to avoid inefficient or circular reasoning patterns.

**中文翻译**: 在策略滚动期间，我们监控推理过程并应用早期终止，以避免低效或循环推理模式。

**解读**:  
- **早期终止（early termination）**: 指在推理无效或重复时提前停止，以提高效率。  
- **低效或循环推理模式（inefficient or circular reasoning patterns）**: 指无意义的重复操作或无进展的推理。

---

**英文**: Specifically, the rollout is terminated and the reward is set to zero when any of the following conditions are met: (1) the model fails to generate any drawing operations, i.e., et = ∅ while rt has not reached a final answer; (2) the number of accumulated images exceeds a predefined threshold α; or (3) a drawing operation duplicates a previously executed one, i.e., ∃t1, t2, u, v : eu t1 = ev t2.

**中文翻译**: 具体而言，当满足以下任一条件时，滚动终止且奖励设为零：(1) 模型未生成任何绘图操作，即 et = ∅ 而 rt 未达到最终答案；(2) 累积图像数量超过预定义阈值 α；或 (3) 绘图操作重复之前执行的操作，即 ∃t1, t2, u, v : eu t1 = ev t2。

**解读**:  
- **终止条件**:  
  1. **无绘图操作（et = ∅）**: 模型未执行视觉操作但推理未结束，表明推理无效。  
  2. **图像数量超限（超过 α）**: 防止生成过多无用图像。  
  3. **操作重复（eu t1 = ev t2）**: 避免重复执行相同的绘图操作。  
- **奖励设为零**: 表示推理路径无效，不予奖励。

---

**英文**: With the rollout policies defined above and reward functions in Eq. 2, we optimize the policy using GRPO [10] without the KL penalty term [20]:  
LRL = E (I,Q,A)∼Drl {Ri}G i=1∼pold(·|I,Q) [−1/G ∑G i=1 1/Ni ∑Ti t=1 min (ρi,t Ai, clip(ρi,t, 1 − ε, 1 + ε) Ai)], (7)  
ρi,t = p(ri,t, ei,t|I, Q, Ri,<t) / pold(ri,t, ei,t|I, Q, Ri,<t), Ai = (Si − mean({Sj }G j=1)) / std({Sj }G j=1), (8)

**中文翻译**: 在上述滚动策略和公式 (2) 的奖励函数下，我们使用 GRPO [10] 优化策略，不使用 KL 惩罚项 [20]：  
LRL = E (I,Q,A)∼Drl {Ri}G i=1∼pold(·|I,Q) [−1/G ∑G i=1 1/Ni ∑Ti t=1 min (ρi,t Ai, clip(ρi,t, 1 − ε, 1 + ε) Ai)], (7)  
ρi,t = p(ri,t, ei,t|I, Q, Ri,<t) / pold(ri,t, ei,t|I, Q, Ri,<t), Ai = (Si − mean({Sj }G j=1)) / std({Sj }G j=1), (8)

**解读**:  
- **GRPO [10]**: 一种强化学习算法（Generalized Advantage Estimation with Proximal Policy Optimization），用于优化模型策略。  
- **无 KL 惩罚项 [20]**: 指不使用 Kullback-Leibler 散度惩罚，以允许更大策略更新幅度。  
- **公式 (7)**: 定义强化学习的损失函数，基于多条推理路径（G 条）的平均奖励。  
- **公式 (8)**:  
  - **ρi,t**: 当前策略 p 与旧策略 pold 的概率比，用于调整学习步长。  
  - **Ai**: 标准化奖励，衡量推理路径 Ri 的相对质量。  
- **clip(ρi,t, 1 − ε, 1 + ε)**: 限制概率比的范围，防止过大的策略更新。  
- **Drl**: 强化学习的数据集，包含输入、问题和答案。

---

**英文**: where G is the number of rollout reasoning paths, Ri = {(ri,t, ei,t, oi,t)}Ti t=1 is the i-th reasoning path, Ni denotes the total length of the Ri except the tool outputs, Si is the reward of Ri, and p and pold represent the current and old policy distributions, respectively.

**中文翻译**: 其中 G 是滚动推理路径的数量，Ri = {(ri,t, ei,t, oi,t)}Ti t=1 是第 i 条推理路径，Ni 表示 Ri 除工具输出外的总长度，Si 是 Ri 的奖励，p 和 pold 分别表示当前和旧的策略分布。

**解读**:  
- **G**: 每次强化学习迭代中采样的推理路径数量。  
- **Ri**: 第 i 条推理路径，包含推理、操作和输出。  
- **Ni**: 推理路径的标记总数，不包括工具输出（oi,t）。  
- **Si**: 根据公式 (2) 计算的奖励。  
- **策略分布（policy distributions）**: 当前策略 p 和旧策略 pold 表示模型生成推理路径的概率分布。

---

**英文**: The normalized score Ai,t reflects the relative quality of each reasoning path within the rollout group, enabling the model to distinguish between learnable and poor reasoning trajectories.

**中文翻译**: 标准化分数 Ai,t 反映了滚动组中每条推理路径的相对质量，使模型能够区分可学习的和较差的推理轨迹。

**解读**:  
- **标准化分数 Ai,t**: 通过公式 (8) 计算，衡量推理路径的优劣。  
- **可学习的推理轨迹（learnable reasoning trajectories）**: 指高质量的推理路径，模型可以从中学习。

---

### 总结

“方法”部分详细描述了“在空间中通过绘图进行推理”的范式和三阶段训练框架。推理范式通过交织自然语言推理和绘图操作（边界框和辅助线），将复杂空间推理任务分解为可解释的步骤。训练框架包括：  
1. **冷启动训练**：使用合成数据集 Dcold 初始化绘图和推理能力。  
2. **反思性拒绝采样**：通过选择性训练增强模型的自我纠错能力。  
3. **强化学习**：使用 GRPO 算法和精心设计的奖励函数优化推理路径。  
奖励函数结合答案正确性和推理格式，采用平均相对精度（MRA）评估数值问题，确保模型在正确性和格式间平衡。反思性拒绝采样通过筛选具有反思行为的路径提升模型能力，强化学习通过滚动策略和标准化奖励进一步优化推理过程。该方法系统性地解决了LVLMs在空间推理中的局限性，提供了创新且高效的训练方案。

以下是对“4 Experiment”部分的逐句翻译和详细解读，包含中英对照，并对关键术语、实验设置、结果和分析进行解释。文中涉及的表格、图表和公式也会在翻译后进行说明。为了保持清晰，每句英文后附上中文翻译，并提供必要的分析。

---

### 4 Experiment

**英文**:  
4.1 Experimental Setups  
Evaluation benchmark and metrics. To evaluate the effectiveness and generalization of VILASR, we conduct experiments on five benchmarks covering three categories:

**中文翻译**:  
4.1 实验设置  
评估基准和指标。为了评估VILASR的有效性和泛化能力，我们在涵盖三个类别的五个基准上进行了实验：

**解读**:  
- **VILASR**: 本文提出的视觉-语言空间推理模型，通过“绘图推理”范式增强空间推理能力。  
- **五个基准（five benchmarks）**: 覆盖图像、视频和多视角空间推理任务，用于全面评估模型性能。  
- **三个类别（three categories）**: 包括图像空间推理、视频空间推理和多视角空间推理。

---

**英文**:  
• Image spatial reasoning: focusing on static relationships and sequential planning, including (1) Maze [25], specifically designed for navigation assessment; (2) SpatialEval-Real [64], demanding real-world spatial relation understanding.

**中文翻译**:  
• 图像空间推理：专注于静态关系和顺序规划，包括 (1) Maze [25]，专为导航评估设计；(2) SpatialEval-Real [64]，要求理解现实世界的空间关系。

**解读**:  
- **图像空间推理（Image spatial reasoning）**: 指基于单张图像的推理任务，涉及静态物体关系（如“左边”）或顺序路径规划（如迷宫导航）。  
- **Maze [25]**: 一个专为测试导航能力的基准，可能涉及在迷宫中规划路径的任务。  
- **SpatialEval-Real [64]**: 测试模型在现实世界场景中理解空间关系的能力，如物体间的距离或方向。  
- **文献引用 [25], [64]**: 提供这两个基准的出处。

---

**英文**:  
• Video spatial reasoning: requiring temporal relationship tracking, including VSI-Bench [69], which tests visual spatial understanding over temporal sequences.

**中文翻译**:  
• 视频空间推理：要求跟踪时间关系，包括 VSI-Bench [69]，测试时间序列上的视觉空间理解。

**解读**:  
- **视频空间推理（Video spatial reasoning）**: 指基于视频序列的推理，需跟踪物体随时间变化的空间关系。  
- **VSI-Bench [69]**: 一个视频空间推理基准，测试模型在动态场景中的表现。  
- **时间序列（temporal sequences）**: 指视频中的连续帧，涉及物体位置或状态的动态变化。  
- **文献引用 [69]**: 提供 VSI-Bench 的出处。

---

**英文**:  
• Multi-view spatial reasoning: challenging models to integrate information from multiple perspectives, including SPAR-Bench [77], MMSI-Bench [70].

**中文翻译**:  
• 多视角空间推理：挑战模型整合多个视角的信息，包括 SPAR-Bench [77]、MMSI-Bench [70]。

**解读**:  
- **多视角空间推理（Multi-view spatial reasoning）**: 指基于多张图像（不同视角）整合空间信息，例如从不同角度推断物体位置。  
- **SPAR-Bench [77], MMSI-Bench [70]**: 两个多视角推理基准，测试模型在复杂场景中的信息整合能力。  
- **文献引用 [77], [70]**: 提供这两个基准的出处。

---

**英文**:  
These benchmarks consist exclusively of multiple-choice and numerical questions.

**中文翻译**:  
这些基准仅包含多选题和数值问题。

**解读**:  
- **多选题和数值问题**: 选择明确答案（如“A. 桌子”）或数值答案（如“3”），便于自动评估。  
- **排除自由形式问题**: 如前文所述，自由形式问题（如描述轨迹）因难以自动评估而未包含。

---

**英文**:  
We evaluate the model performance using accuracy for multiple-choice questions and Mean Relative Accuracy (MRA) [69] for numerical questions.

**中文翻译**:  
我们使用准确率评估多选题的性能，使用平均相对精度（MRA）[69]评估数值问题的性能。

**解读**:  
- **准确率（accuracy）**: 多选题的评估指标，计算预测答案与真实答案的匹配比例。  
- **平均相对精度（MRA）**: 数值问题的评估指标，基于相对误差在多个置信度阈值下的表现（如公式 3）。  
- **文献引用 [69]**: 指 MRA 的出处。

---

**英文**:  
Notably, these metrics follow the same formulation as our training objective (Eq. 3).

**中文翻译**:  
值得注意的是，这些指标遵循与我们训练目标相同的公式（公式 3）。

**解读**:  
- **公式 3**: 定义了训练中的正确性分数（Scorrect），与评估指标一致，确保训练和评估目标对齐。  
- **训练目标（training objective）**: 指通过最大化 Scorrect 和 Sformat 优化模型。

---

**英文**:  
Appendix C.2 shows the benchmark statistics.

**中文翻译**:  
附录 C.2 显示基准统计数据。

**解读**:  
- **基准统计数据（benchmark statistics）**: 可能包括数据集规模、问题类型分布等详细信息，位于附录 C.2。

---

**英文**:  
Implementation details. We implement VILASR based on Qwen2.5-VL-7B [2].

**中文翻译**:  
实现细节。我们基于 Qwen2.5-VL-7B [2] 实现 VILASR。

**解读**:  
- **Qwen2.5-VL-7B [2]**: 一个开源的视觉-语言模型（7亿参数），作为 VILASR 的基础模型。  
- **文献引用 [2]**: 提供 Qwen2.5-VL-7B 的出处。

---

**英文**:  
During the training phase, we process all visual inputs at a maximum resolution of 256 × 28 × 28, with video clips uniformly sampled at 16 frames.

**中文翻译**:  
在训练阶段，我们以最大分辨率 256 × 28 × 28 处理所有视觉输入，视频片段均匀采样为 16 帧。

**解读**:  
- **分辨率 256 × 28 × 28**: 指图像或视频帧的处理分辨率，可能是笔误，应为 256 × 256 或类似标准分辨率（需参考原文或附录）。  
- **均匀采样 16 帧**: 指从视频中均匀选择 16 帧作为输入，简化计算复杂度。

---

**英文**:  
In the evaluation stage, we maintain the 16-frame count and the 256 × 28 × 28 frame resolution for VSI-Bench, while increase the resolution to 448 × 28 × 28 for other benchmarks.

**中文翻译**:  
在评估阶段，我们对 VSI-Bench 保持 16 帧和 256 × 28 × 28 帧分辨率，而对其他基准提高分辨率至 448 × 28 × 28。

**解读**:  
- **评估阶段分辨率**: VSI-Bench 使用较低分辨率（256 × 28 × 28，可能为笔误），其他基准使用更高分辨率（448 × 28 × 28）以捕捉更多细节。  
- **16 帧**: 保持视频输入的一致性。

---

**英文**:  
The training is conducted on a cluster of 16 NVIDIA A100 (80G) GPUs.

**中文翻译**:  
训练在 16 个 NVIDIA A100 (80G) GPU 的集群上进行。

**解读**:  
- **NVIDIA A100 (80G)**: 高性能 GPU，用于支持大规模模型训练。  
- **16 个 GPU 集群**: 表明训练需要大量计算资源。

---

**英文**:  
For both cold-start training stage and reflective fine-tuning stage, we optimize the model with a learning rate of 1 × 10−5 for three epochs, requiring approximately 24 and 3 hours, respectively.

**中文翻译**:  
对于冷启动训练阶段和反思性微调阶段，我们以 1 × 10−5 的学习率优化模型，进行三个周期，分别需要大约 24 小时和 3 小时。

**解读**:  
- **学习率 1 × 10−5**: 较小的学习率，确保模型稳定优化。  
- **三个周期（three epochs）**: 指数据集完整训练三遍。  
- **训练时间**: 冷启动训练耗时较长（24 小时），反思性微调较短（3 小时），可能因数据集规模不同。

---

**英文**:  
The subsequent RL optimization is implemented using the VERL framework [57], where we set the training batch size to 32 and generate 8 candidate reasoning paths per question.

**中文翻译**:  
后续强化学习优化使用 VERL 框架 [57] 实现，我们设置训练批次大小为 32，并为每个问题生成 8 条候选推理路径。

**解读**:  
- **VERL 框架 [57]**: 一种强化学习框架，可能专门用于优化视觉-语言模型。  
- **批次大小 32**: 每次训练处理 32 个样本。  
- **8 条候选推理路径**: 每个问题生成多个推理路径，供强化学习优化选择。  
- **文献引用 [57]**: 提供 VERL 框架的出处。

---

**英文**:  
We set the maximum cumulative image number α to 42.

**中文翻译**:  
我们将最大累积图像数量 α 设为 42。

**解读**:  
- **最大累积图像数量 α**: 指推理过程中生成的最大标注图像数量，防止过多无用图像（如 3.2 节所述）。

---

**英文**:  
And the reward threshold β in Eq. 2 is set to 0.0.

**中文翻译**:  
公式 (2) 中的奖励阈值 β 设为 0.0。

**解读**:  
- **奖励阈值 β**: 用于确保只有答案正确性达到一定水平时才考虑格式奖励。设为 0.0 表示任何正确性得分都可获得格式奖励，可能简化训练。

---

**英文**:  
The training dynamics are shown in Figure 3.

**中文翻译**:  
训练动态如图 3 所示。

**解读**:  
- **训练动态（training dynamics）**: 指训练过程中模型性能（如奖励分数）的变化趋势。  
- **图 3**: 可能展示奖励分数 Scorrect、Sformat 和总奖励 S 的随时间变化曲线。

---

**英文**:  
As illustrated in (a-c), both overall reward S and its components (Scorrect and Sformat) demonstrate steady improvements, validating the effectiveness of our RL optimization.

**中文翻译**:  
如图 (a-c) 所示，总奖励 S 及其组成部分（Scorrect 和 Sformat）均显示出稳步提升，验证了我们强化学习优化的有效性。

**解读**:  
- **总奖励 S**: 由公式 (2) 定义，结合正确性和格式分数。  
- **Scorrect 和 Sformat**: 分别表示答案正确性和推理格式的得分。  
- **稳步提升（steady improvements）**: 表明强化学习有效提高了模型性能。

---

**英文**:  
Notably, while achieving better task performance, we observe a decrease in response length N from 2,500 to 1,800 tokens (d).

**中文翻译**:  
值得注意的是，在实现更好任务性能的同时，我们观察到响应长度 N 从 2,500 个标记减少到 1,800 个标记（图 d）。

**解读**:  
- **响应长度 N**: 指推理路径中的标记总数（包括推理文本和绘图操作）。  
- **从 2,500 到 1,800**: 表明强化学习优化使模型推理更高效，减少了冗余步骤。  
- **图 d**: 可能展示响应长度随训练变化的曲线。

---

**英文**:  
This can be attributed to two factors: First, during cold-start training, we set a minimum of three reasoning steps in synthetic data to encourage in-depth reasoning, while RL optimization subsequently drives the model toward more efficient use of drawing operations.

**中文翻译**:  
这可以归因于两个因素：首先，在冷启动训练期间，我们在合成数据中设置了最少三个推理步骤以鼓励深入推理，而强化学习优化随后推动模型更高效地使用绘图操作。

**解读**:  
- **最少三个推理步骤**: 冷启动训练鼓励模型进行多步推理，增加响应长度。  
- **更高效的绘图操作**: 强化学习优化模型选择更简洁的操作，减少不必要的步骤。

---

**英文**:  
Second, the limited training data may not fully expose the model to complex scenarios requiring lengthy reasoning chains.

**中文翻译**:  
其次，有限的训练数据可能无法完全暴露模型于需要冗长推理链的复杂场景。

**解读**:  
- **有限训练数据（limited training data）**: 指数据集的多样性不足，可能缺乏复杂空间推理任务。  
- **冗长推理链（lengthy reasoning chains）**: 指处理复杂任务所需的更多推理步骤。

---

**英文**:  
We expect that increasing training data diversity could potentially lead to longer but necessary reasoning steps for more challenging spatial tasks [67].

**中文翻译**:  
我们预期增加训练数据的多样性可能导致更长但必要的推理步骤，以应对更具挑战性的空间任务 [67]。

**解读**:  
- **训练数据多样性（training data diversity）**: 指包含更多样化场景和任务的数据集。  
- **更具挑战性的空间任务**: 如复杂的迷宫导航或多视角推理。  
- **文献引用 [67]**: 支持数据多样性对复杂任务推理的影响。

---

**英文**:  
Baselines. We compare VILASR with various representative models and methods as follows:

**中文翻译**:  
基线。我们将 VILASR 与以下各种代表性模型和方法进行比较：

**解读**:  
- **基线（Baselines）**: 指用于比较的现有模型和方法，包括专有模型和开源模型。

---

**英文**:  
• Proprietary LVLMs: GPT-4o [43], Gemini-1.5-Pro [61], Gemini-2.0-Flash [16], OpenAI o3 and o4-mini [45];

**中文翻译**:  
• 专有 LVLMs：GPT-4o [43]、Gemini-1.5-Pro [61]、Gemini-2.0-Flash [16]、OpenAI o3 和 o4-mini [45]；

**解读**:  
- **专有 LVLMs（Proprietary LVLMs）**: 指商业开发的视觉-语言模型，通常性能较强但不公开源代码。  
- **文献引用 [43, 61, 16, 45]**: 提供这些模型的出处。

---

**英文**:  
• Open-source LVLMs: These models range from small-sized models including Qwen2.5-VL-7B [2], LLaVA-NeXT-Video-7B [79] and LLaVA-OneVision-7B [30] to large-sized models including Kimi-VL-A3B-Instruct (16B) [62], Qwen2.5-VL-72B [2], LLaVA-NeXT-Video-72B [79], LLaVA-OneVision-72B [30];

**中文翻译**:  
• 开源 LVLMs：这些模型包括小型模型，如 Qwen2.5-VL-7B [2]、LLaVA-NeXT-Video-7B [79] 和 LLaVA-OneVision-7B [30]，以及大型模型，如 Kimi-VL-A3B-Instruct (16B) [62]、Qwen2.5-VL-72B [2]、LLaVA-NeXT-Video-72B [79]、LLaVA-OneVision-72B [30]；

**解读**:  
- **开源 LVLMs**: 公开源代码的视觉-语言模型，参数规模从小（7亿）到大（72亿）。  
- **小型模型 vs. 大型模型**: 小型模型计算需求较低，大型模型性能更强但资源消耗大。  
- **文献引用 [2, 79, 30, 62]**: 提供这些模型的出处。

---

**英文**:  
• Representative models focused on multimodal reasoning: COGCOM [50], which enables step-by-step visual reasoning through image manipulations with specialized perception tools (e.g., grounding) but is limited to single-image inputs; VisCoT [54], which first identifies key regions through bounding box annotations followed by textual reasoning chains on single images; and SpaceR [47], which is a contemporary work that extends spatial reasoning to video understanding through task-specific optimization on automatically curated video QA data.

**中文翻译**:  
• 专注于多模态推理的代表性模型：COGCOM [50]，通过使用专用感知工具（例如定位）进行图像操作实现逐步视觉推理，但局限于单张图像输入；VisCoT [54]，首先通过边界框标注识别关键区域，然后在单张图像上进行文本推理链；以及 SpaceR [47]，一项当代工作，通过在自动整理的视频问答数据上进行任务特定优化，将空间推理扩展到视频理解。

**解读**:  
- **COGCOM [50]**: 使用外部感知工具（如目标检测）进行视觉推理，局限在于仅支持单张图像。  
- **VisCoT [54]**: 先标注边界框再进行文本推理，缺乏反思能力。  
- **SpaceR [47]**: 专注于视频空间推理，通过特定任务优化，但仍以文本为中心。  
- **文献引用 [50, 54, 47]**: 提供这些模型的出处。

---

**英文**:  
Furthermore, we perform ablation studies to evaluate each individual training stage to assess their contributions to the final performance.

**中文翻译**:  
此外，我们进行消融研究以评估每个训练阶段对最终性能的贡献。

**解读**:  
- **消融研究（ablation studies）**: 通过逐一移除训练阶段，分析每个阶段的作用。

---

**英文**:  
Implementation details of the baselines are shown in Appendix C.1.

**中文翻译**:  
基线的实现细节显示在附录 C.1 中。

**解读**:  
- **附录 C.1**: 提供基线模型的详细设置，如训练参数或数据处理方式。

---

### 4.2 Main Results

**英文**:  
As shown in Table 1, VILASR shows strong performance across various spatial reasoning benchmarks, from maze navigation to complex video understanding.

**中文翻译**:  
如表 1 所示，VILASR 在各种空间推理基准上表现出色，从迷宫导航到复杂视频理解。

**解读**:  
- **表 1**: 展示了 VILASR 与基线模型在五个基准上的性能比较。  
- **强性能（strong performance）**: 表明 VILASR 在多个任务中优于其他模型。

---

**英文**:  
Our analysis reveals several key findings:

**中文翻译**:  
我们的分析揭示了几个关键发现：

**解读**:  
以下是实验结果的主要分析点。

---

**英文**:  
(1) Limited visual reasoning capabilities in open-source LLMs. Our experiments reveal a significant disparity between proprietary and open-source LLMs in their ability to leverage reasoning processes.

**中文翻译**:  
(1) 开源 LLMs 的视觉推理能力有限。我们的实验揭示了专有模型和开源 LLMs 在利用推理过程能力上的显著差异。

**解读**:  
- **视觉推理能力有限（limited visual reasoning capabilities）**: 开源模型在多模态推理上表现不如专有模型。  
- **专有 vs. 开源 LLMs**: 专有模型（如 GPT-4o）在推理能力上更强。

---

**英文**:  
Proprietary models consistently outperform their non-reasoning counterparts by a substantial margin across different benchmarks (e.g., GPT-4o, Gemini-2.0-Flash).

**中文翻译**:  
专有模型在不同基准上始终大幅优于其无推理的对应模型（例如 GPT-4o、Gemini-2.0-Flash）。

**解读**:  
- **专有模型优于无推理模型**: 表明推理能力（如慢思考）显著提升专有模型性能。  
- **大幅（substantial margin）**: 指性能差距明显。

---

**英文**:  
However, open-source models like Qwen2.5-VL-7B show minimal or even negative improvements with reasoning enabled, suggesting a significant gap in their fundamental visual reasoning capabilities.

**中文翻译**:  
然而，像 Qwen2.5-VL-7B 这样的开源模型在启用推理后改进极小甚至呈负值，表明其基本视觉推理能力存在显著差距。

**解读**:  
- **负改进（negative improvements）**: 指推理过程可能引入错误，导致性能下降。  
- **基本视觉推理能力差距**: 开源模型在多模态推理的基础能力上较弱。

---

**英文**:  
This observation highlights a critical direction for future research: enhancing the multimodal reasoning abilities of open-source models, potentially through improved architectural designs and more sophisticated training strategies that better integrate visual and linguistic information.

**中文翻译**:  
这一观察结果突显了未来研究的关键方向：通过改进架构设计和更复杂的训练策略，增强开源模型的多模态推理能力，更好地整合视觉和语言信息。

**解读**:  
- **未来研究方向**: 指改进开源模型的多模态推理能力，如优化模型结构或训练方法。  
- **整合视觉和语言信息**: 指模型需更有效地处理图像和文本的联合表示。

---

**英文**:  
(2) Strong performance of VILASR on image-based spatial tasks. VILASR demonstrates exceptional capabilities in both sequential spatial planning (MAZE) and static spatial understanding (SpatialEval).

**中文翻译**:  
(2) VILASR 在基于图像的空间任务上的强大性能。VILASR 在顺序空间规划（Maze）和静态空间理解（SpatialEval）上表现出卓越能力。

**解读**:  
- **顺序空间规划（sequential spatial planning）**: 指如迷宫导航的逐步推理任务。  
- **静态空间理解（static spatial understanding）**: 指分析单张图像中的空间关系。  
- **卓越能力（exceptional capabilities）**: 表明 VILASR 在图像任务上表现突出。

---

**英文**:  
The remarkable performance on maze navigation, in particular, highlights the advantage of our “drawing to reason in space” paradigm: through iterative drawing operations, the model effectively breaks down multi-step navigation sequences into interpretable visual steps, thereby capturing and tracking spatial state transitions.

**中文翻译**:  
特别是在迷宫导航上的出色表现，突显了我们“在空间中通过绘图进行推理”范式的优势：通过迭代绘图操作，模型有效将多步导航序列分解为可解释的视觉步骤，从而捕捉和跟踪空间状态转换。

**解读**:  
- **绘图推理范式**: 通过边界框和辅助线分解复杂任务。  
- **可解释的视觉步骤（interpretable visual steps）**: 指绘图操作使推理过程清晰可见。  
- **空间状态转换（spatial state transitions）**: 指物体或路径在空间中的变化，如迷宫中的移动。

---

**英文**:  
In contrast, existing methods show limited performance due to various constraints: COGCOM is restricted by the capabilities of its perception tools, and VisCoT lacks the ability to reflect and revise its visual operations since it only performs one-time grounding.

**中文翻译**:  
相比之下，现有方法由于各种限制表现有限：COGCOM 受限于其感知工具的能力，VisCoT 缺乏反思和修正视觉操作的能力，因为它仅执行一次定位。

**解读**:  
- **COGCOM 的限制**: 依赖外部感知工具（如目标检测），性能受工具限制。  
- **VisCoT 的局限**: 仅进行一次边界框标注，缺乏动态调整能力。

---

**英文**:  
(3) Competitive results of VILASR on video and multi-view reasoning. Video and multi-view reasoning present unique challenges beyond static image understanding, as it requires tracking spatial relationships across multiple viewpoints and temporal transitions.

**中文翻译**:  
(3) VILASR 在视频和多视角推理上的竞争性结果。视频和多视角推理提出了超越静态图像理解的独特挑战，因为它需要跟踪多个视角和时间转换中的空间关系。

**解读**:  
- **视频和多视角推理的挑战**: 涉及动态和多视角的空间关系，比静态图像任务更复杂。  
-COMMUNITY: **竞争性结果（competitive results）**: 表明 VILASR 在这些任务上表现优异，与其他模型相比具有竞争力。

---

**英文**:  
While most existing models struggle with this increased complexity, VILASR achieves state-of-the-art performance on all benchmarks, surpassing significantly larger open-source models such as LLaVA-OneVision-72B.

**中文翻译**:  
虽然大多数现有模型难以应对这种复杂性增加，VILASR 在所有基准上实现了最先进的性能，超越了如 LLaVA-OneVision-72B 这样明显更大的开源模型。

**解读**:  
- **最先进的性能（state-of-the-art performance）**: 指 VILASR 在所有基准上领先。  
- **超越更大模型**: 表明 VILASR（基于 7B 参数）优于更大模型（如 72B 参数的 LLaVA-OneVision），显示其高效性。

---

**英文**:  
This success can be attributed to our flexible visual operations that effectively handle dynamic spatial relationships.

**中文翻译**:  
这一成功归因于我们灵活的视觉操作，有效处理动态空间关系。

**解读**:  
- **灵活的视觉操作（flexible visual operations）**: 指边界框和辅助线的迭代使用，适应动态场景。  
- **动态空间关系（dynamic spatial relationships）**: 指视频或多视角中随时间或视角变化的空间关系。

---

**英文**:  
In contrast, existing approaches face fundamental limitations: COGCOM and VisCoT lack video processing capabilities entirely, while SpaceR’s text-centric reasoning fails to fully exploit visual temporal information.

**中文翻译**:  
相比之下，现有方法面临根本性限制：COGCOM 和 VisCoT 完全缺乏视频处理能力，而 SpaceR 的文本中心推理无法充分利用视觉时间信息。

**解读**:  
- **COGCOM 和 VisCoT 的局限**: 仅支持单张图像，无法处理视频。  
- **SpaceR 的局限**: 依赖文本推理，未能有效利用视频中的时间信息。

---

### 4.3 Ablation Study

**英文**:  
To comprehensively evaluate our training framework, we conduct ablation studies on VSI-Bench’s eight spatial reasoning subtasks and analyze four key behavioral metrics.

**中文翻译**:  
为了全面评估我们的训练框架，我们在 VSI-Bench 的八个空间推理子任务上进行消融研究，并分析四个关键行为指标。

**解读**:  
- **消融研究（ablation studies）**: 通过移除训练阶段（如冷启动、反思性拒绝采样或强化学习），评估每个阶段的贡献。  
- **VSI-Bench 的八个子任务**: 可能包括物体计数、距离测量等具体任务（见图 4a）。  
- **行为指标（behavioral metrics）**: 用于评估模型推理行为的特性。

---

**英文**:  
The behavioral metrics include: (1) Reflection Pattern Exhibition, measuring the ratio of examples exhibiting reflection behavior as defined in Eq. 5; (2) Number of Reasoning Steps, indicating the average number of reasoning steps (T) required to answer each question; and (3,4) Numbers of Tbox and Tline, reflecting the average number of drawing operations utilized per question.

**中文翻译**:  
行为指标包括：(1) 反思模式展示，测量展示公式 (5) 定义的反思行为的样本比例；(2) 推理步骤数，指示回答每个问题所需的平均推理步骤数（T）；以及 (3,4) Tbox 和 Tline 的数量，反映每个问题使用的平均绘图操作数。

**解读**:  
- **反思模式展示（Reflection Pattern Exhibition）**: 指满足公式 (5) 反思定义的样本比例，即重复标注同一物体但调整操作。  
- **推理步骤数（Number of Reasoning Steps）**: 指推理路径的长度 T。  
- **Tbox 和 Tline 的数量**: 分别指边界框和辅助线的平均使用次数。

---

**英文**:  
The results are shown in Figure 4(a) for task performance and Figure 4(b) for behavioral patterns.

**中文翻译**:  
结果如图 4(a) 所示为任务性能，图 4(b) 所示为行为模式。

**解读**:  
- **图 4(a)**: 展示各子任务的性能变化（如分数变化）。  
- **图 4(b)**: 展示行为指标的相对变化（如反思行为比例）。

---

**英文**:  
We draw the following insights:  
(1) Cold-start training: Essential for spatial reasoning foundation.

**中文翻译**:  
我们得出以下见解：  
(1) 冷启动训练：空间推理基础的关键。

**解读**:  
- **冷启动训练**: 为模型提供绘图和推理的基础能力。

---

**英文**:  
Comparing “VILASR w/o Stage 1&2&3” with “VILASR w/o Stage 2&3”, we observe substantial performance improvements across all subtasks.

**中文翻译**:  
比较“VILASR w/o Stage 1&2&3”和“VILASR w/o Stage 2&3”，我们观察到所有子任务的性能显著提升。

**解读**:  
- **VILASR w/o Stage 1&2&3**: 仅使用 Qwen2.5-VL-7B 基础模型，无任何训练。  
- **VILASR w/o Stage 2&3**: 仅进行冷启动训练。  
- **显著提升**: 表明冷启动训练为空间推理奠定了基础。

---

**英文**:  
Notably, when equipped with only our “drawing to reason in space” paradigm without training (i.e., “VILASR w/o Stage 1&2&3”), the model performs even worse than the Qwen2.5-VL-7B backbone.

**中文翻译**:  
值得注意的是，仅配备我们的“在空间中通过绘图进行推理”范式而无训练（即“VILASR w/o Stage 1&2&3”）时，模型表现甚至不如 Qwen2.5-VL-7B 基础模型。

**解读**:  
- **无训练的范式**: 仅靠提示无法实现有效空间推理，强调训练的必要性。  
- **不如基础模型**: 表明未经训练的绘图推理可能引入错误。

---

**英文**:  
This degradation highlights that sophisticated spatial reasoning capabilities cannot emerge solely with prompting but must be learned through dedicated training.

**中文翻译**:  
这种性能下降表明，复杂空间推理能力无法仅通过提示浮现，必须通过专门训练学习。

**解读**:  
- **提示的局限性**: 提示工程不足以激发空间推理能力。  
- **专门训练（dedicated training）**: 指冷启动训练等专门设计的训练过程。

---

**英文**:  
(2) Reflection sampling: Key to self-correction ability.

**中文翻译**:  
(2) 反思性拒绝采样：自我纠错能力的关键。

**解读**:  
- **反思性拒绝采样**: 通过筛选具有反思行为的推理路径，增强模型自我纠错能力。

---

**英文**:  
The comparison between VILASR and “VILASR w/o Stage 2” reveals the crucial role of reflective rejection sampling.

**中文翻译**:  
VILASR 与“VILASR w/o Stage 2”的比较揭示了反思性拒绝采样的关键作用。

**解读**:  
- **VILASR w/o Stage 2**: 缺少反思性拒绝采样阶段。  
- **关键作用**: 表明反思性拒绝采样显著提升性能。

---

**英文**:  
Removing this stage leads to a 96.5% decrease in reflection pattern exhibition, fundamentally altering the model’s behavior and performance.

**中文翻译**:  
移除此阶段导致反思模式展示下降 96.5%，从根本上改变了模型的行为和性能。

**解读**:  
- **96.5% 下降**: 表明反思行为几乎消失，严重影响模型能力。  
- **行为和性能变化**: 缺乏反思导致推理过程不完整。

---

**英文**:  
Behaviorally, we observe a 33.9% reduction in reasoning steps and dramatically different patterns in drawing operation usage: a 85.0% decrease in Tbox but a 70.5% increase in Tline.

**中文翻译**:  
在行为上，我们观察到推理步骤减少 33.9%，绘图操作使用模式发生显著变化：Tbox 减少 85.0%，但 Tline 增加 70.5%。

**解读**:  
- **推理步骤减少 33.9%**: 缺乏反思导致推理过程简化，可能是错误的简化。  
- **Tbox 减少 85.0%**: 边界框使用大幅减少，可能因模型无法有效定位物体。  
- **Tline 增加 70.5%**: 辅助线使用增加，可能因模型倾向于简单方向判断。

---

**英文**:  
Such changes particularly affect tasks requiring precise object localization and measurement: “Absolute Distance” (-0.6%), “Room Size” (-0.7%), and “Relative Distance” (-1.0%).

**中文翻译**:  
这些变化尤其影响需要精确物体定位和测量的任务：“绝对距离”（-0.6%）、“房间大小”（-0.7%）和“相对距离”（-1.0%）。

**解读**:  
- **精确物体定位和测量**: 指需要准确确定物体位置或距离的任务，依赖边界框。  
- **性能下降**: 表明反思性拒绝采样对这些任务至关重要。

---

**英文**:  
In contrast, tasks that primarily rely on directional judgment or categorical reasoning show minimal impact or even slight improvements (e.g., “Object Count”: +0.1%, “Relative Direction”: +0.9%), as they can be solved with simpler spatial relationships indicated by lines.

**中文翻译**:  
相比之下，主要依赖方向判断或分类推理的任务影响较小，甚至略有改进（例如“物体计数”：+0.1%，“相对方向”：+0.9%），因为这些任务可以通过线条指示的简单空间关系解决。

**解读**:  
- **方向判断或分类推理**: 指如判断“左边”或计数物体等任务，依赖辅助线而非精确定位。  
- **较小影响**: 表明这些任务对反思行为的需求较低。

---

**英文**:  
This pattern reveals that reflection capability fundamentally shapes how the model builds spatial understanding.

**中文翻译**:  
这种模式表明，反思能力从根本上塑造了模型构建空间理解的方式。

**解读**:  
- **反思能力（reflection capability）**: 指模型通过检查和修正操作构建更准确的空间理解。

---

**英文**:  
Without it, the model shows a tendency to make quick spatial judgments through auxiliary lines without sufficient self-verification.

**中文翻译**:  
没有反思能力，模型倾向于通过辅助线进行快速空间判断，缺乏充分的自我验证。

**解读**:  
- **快速空间判断（quick spatial judgments）**: 指模型直接使用辅助线判断方向或关系，未经检查。  
- **自我验证（self-verification）**: 指反思性检查操作的正确性。

---

**英文**:  
Based on this observation, we hypothesize specific mechanisms through which reflection enhances spatial reasoning: re-examining object locations through bbox annotations and carefully evaluating different spatial relationships before making final judgments (see examples in Appendix §D).

**中文翻译**:  
基于这一观察，我们假设反思通过以下特定机制增强空间推理：通过边界框标注重新检查物体位置，并在做出最终判断前仔细评估不同的空间关系（见附录 §D 中的示例）。

**解读**:  
- **反思机制**: 包括重新检查物体位置（边界框）和评估空间关系（辅助线）。  
- **附录 §D**: 提供反思行为的示例，可能展示具体推理路径。

---

**英文**:  
This verification-driven approach, rather than making multiple “guessing” attempts through auxiliary lines, appears to be key to accurate spatial reasoning.

**中文翻译**:  
这种验证驱动的方法，而非通过辅助线进行多次“猜测”尝试，似乎是准确空间推理的关键。

**解读**:  
- **验证驱动（verification-driven）**: 指通过反思和修正确保推理准确。  
- **猜测尝试（guessing attempts）**: 指未经验证的快速操作，可能导致错误。

---

**英文**:  
(3) RL optimization: Dense rewards enable fine-grained learning.

**中文翻译**:  
(3) 强化学习优化：密集奖励实现精细学习。

**解读**:  
- **强化学习优化（RL optimization）**: 指通过密集奖励函数优化推理过程。  
- **密集奖励（dense rewards）**: 指为每个推理步骤提供奖励，而非仅奖励最终答案。

---

**英文**:  
Comparing VILASR with “VILASR w/o Stage 3”, we observe consistent performance decreases across most subtasks.

**中文翻译**:  
比较 VILASR 与“VILASR w/o Stage 3”，我们观察到大多数子任务的性能一致下降。

**解读**:  
- **VILASR w/o Stage 3**: 缺少强化学习阶段。  
- **性能下降**: 表明强化学习对性能提升至关重要。

---

**英文**:  
The substantial increases in both Tbox (+159.4%) and Tline (+9.1%) usage without RL suggest that RL optimization helps the model learn to use drawing operations more selectively.

**中文翻译**:  
没有强化学习时，Tbox（+159.4%）和 Tline（+9.1%）使用量大幅增加，表明强化学习优化帮助模型更选择性地使用绘图操作。

**解读**:  
- **Tbox 和 Tline 增加**: 缺少强化学习导致操作冗余。  
- **选择性使用（more selectively）**: 强化学习使模型更精准地选择必要的绘图操作。

---

**英文**:  
Moreover, tasks requiring precise numerical answers (“Object Count,” “Absolute Distance,” “Object Size” and “Room Size”) show greater average performance gaps without RL compared to multiple-choice questions (-9.21% vs. -4.07%).

**中文翻译**:  
此外，需要精确数值答案的任务（“物体计数”、“绝对距离”、“物体大小”和“房间大小”）在没有强化学习时表现出更大的平均性能差距，相比多选题（-9.21% vs. -4.07%）。

**解读**:  
- **精确数值答案**: 指需要准确计数的任务，依赖精细的空间推理。  
- **更大性能差距**: 表明强化学习对数值任务的优化效果更显著。  
- **-9.21% vs. -4.07%**: 数值任务的性能下降更严重，凸显强化学习的作用。

---

**英文**:  
This disparity highlights a key advantage of RL optimization: while supervised learning merely maximizes the probability of correct answers, RL provides dense reward signals based on numerical proximity to ground truth, enabling more effective learning for precise spatial measurements.

**中文翻译**:  
这种差异突显了强化学习优化的关键优势：监督学习仅最大化正确答案的概率，而强化学习基于与真实值的数值接近度提供密集奖励信号，使精确空间测量更有效的学习。

**解读**:  
- **密集奖励信号（dense reward signals）**: 指为每个推理步骤提供奖励，基于答案与真实值的接近程度。  
- **精确空间测量（precise spatial measurements）**: 指如距离或物体计数的精确推理。

---

### 4.4 Inference-time Scaling

**英文**:  
We further evaluate the effectiveness of our training framework through the lens of inference-time scaling analysis such as pass@k evaluation (sampling k outputs in parallel and selecting the best).

**中文翻译**:  
我们通过推理时间扩展分析（如 pass@k 评估，平行采样 k 个输出并选择最佳）进一步评估训练框架的有效性。

**解读**:  
- **推理时间扩展分析（inference-time scaling analysis）**: 指测试模型在不同采样次数（k）下的性能。  
- **pass@k**: 指从 k 个输出中选择最佳答案的准确率，反映模型的多尝试能力。

---

**英文**:  
Prior research has demonstrated: (1) pass@k serves as an empirical upper bound of model capability with sufficiently large k [58], while pass@1 reflects its single-attempt performance; (2) RL has been shown to effectively narrow this gap by consolidating pass@k capabilities into pass@1 performance [75].

**中文翻译**:  
先前研究表明：(1) pass@k 在 k 足够大时作为模型能力的经验上限 [58]，而 pass@1 反映其单次尝试性能；(2) 强化学习已证明能通过将 pass@k 能力整合到 pass@1 性能，有效缩小这一差距 [75]。

**解读**:  
- **pass@k 的经验上限**: 大 k 值下，pass@k 接近模型的最大潜力。  
- **pass@1**: 单次推理的准确率，反映实际应用性能。  
- **强化学习缩小差距**: RL 优化使单次推理接近多尝试的最佳性能。  
- **文献引用 [58, 75]**: 支持 pass@k 和 RL 优化的研究。

---

**英文**:  
These insights motivate us to examine how each training stage contributes to expanding model capability.

**中文翻译**:  
这些见解激励我们检查每个训练阶段如何有助于扩展模型能力。

**解读**:  
- **扩展模型能力（expanding model capability）**: 指提高模型在单次和多次尝试下的性能。

---

**英文**:  
Results in Figure 5 reveal the progressive enhancement of model capability across training stages: (1) Cold-start training substantially improves both the empirical upper bound (pass@8) and single-attempt performance (pass@1) compared to Qwen2.5-VL-7B;

**中文翻译**:  
图 5 的结果显示训练阶段的模型能力逐步增强：(1) 冷启动训练与 Qwen2.5-VL-7B 相比，大幅提高了经验上限（pass@8）和单次尝试性能（pass@1）；

**解读**:  
- **图 5**: 展示 pass@1 和 pass@8 的性能变化。  
- **冷启动训练**: 显著提升模型的基础推理能力。

---

**英文**:  
(2) Reflective rejection sampling further elevates both metrics, demonstrating expanded reasoning potential;

**中文翻译**:  
(2) 反思性拒绝采样进一步提升了这两个指标，展示了扩展的推理潜力；

**解读**:  
- **反思性拒绝采样**: 通过增强自我纠错能力，进一步提高模型性能。  
- **扩展的推理潜力（expanded reasoning potential）**: 指模型能够处理更复杂的推理任务。

---

**英文**:  
(3) RL optimization not only pushes the empirical upper bound (pass@8) but also significantly narrows the gap with single-attempt performance (pass@1), indicating effective consolidation of multi-attempt capabilities that aligns with previous studies about RL’s optimization effects [75].

**中文翻译**:  
(3) 强化学习优化不仅推动了经验上限（pass@8），还显著缩小了与单次尝试性能（pass@1）的差距，表明有效整合了多次尝试能力，与之前关于强化学习优化效果的研究一致 [75]。

**解读**:  
- **强化学习优化**: 提高多尝试能力并将其整合到单次推理中。  
- **缩小差距**: pass@1 接近 pass@8，表明模型单次推理更接近最佳性能。  
- **文献引用 [75]**: 提供 RL 优化效果的支持。

---

### 5 Conclusion

**英文**:  
This work presents a principled approach to enhancing spatial reasoning capabilities in LVLMs through visual drawing operations.

**中文翻译**:  
本工作提出了通过视觉绘图操作增强 LVLMs 空间推理能力的原则性方法。

**解读**:  
- **原则性方法（principled approach）**: 指系统化的“绘图推理”范式和三阶段训练框架。  
- **视觉绘图操作（visual drawing operations）**: 指边界框和辅助线，用于直接操作视觉空间。

---

**英文**:  
By enabling direct manipulation in the visual space through the “drawing to reason in space” paradigm, we bridge the gap between text-centric reasoning and human-like spatial cognition.

**中文翻译**:  
通过“在空间中通过绘图进行推理”范式实现视觉空间的直接操作，我们弥合了以文本为中心推理与类人空间认知之间的差距。

**解读**:  
- **直接操作视觉空间（direct manipulation in the visual space）**: 指通过绘图操作直接处理图像，而非依赖文本转化。  
- **类人空间认知（human-like spatial cognition）**: 模仿人类通过心理可视化进行空间推理的能力。

---

**英文**:  
Through careful empirical validation, we demonstrate that our three-stage training framework successfully cultivates sophisticated reasoning pattern.

**中文翻译**:  
通过仔细的实验验证，我们证明了我们的三阶段训练框架成功培养了复杂的推理模式。

**解读**:  
- **三阶段训练框架**: 冷启动训练、反思性拒绝采样和强化学习。  
- **复杂推理模式（sophisticated reasoning pattern）**: 指迭代绘图和反思性推理的结合。

---

**英文**:  
Extensive experiments across diverse spatial reasoning benchmarks validate the effectiveness of our approach, showing particular strengths in maze navigation and temporal-spatial understanding tasks.

**中文翻译**:  
跨越多个空间推理基准的广泛实验验证了我们方法的有效性，特别是在迷宫导航和时间-空间理解任务中表现出特别的优势。

**解读**:  
- **广泛实验（extensive experiments）**: 指在五个基准上的测试。  
- **迷宫导航和时间-空间理解**: VILASR 在动态和顺序推理任务中表现突出。

---

**英文**:  
While our results are promising, several important directions remain for future exploration, such as extending our drawing operations to handle more complex 3D spatial relationships, and investigating more efficient training strategies.

**中文翻译**:  
虽然我们的结果令人鼓舞，但仍有几个重要的未来探索方向，如扩展绘图操作以处理更复杂的 3D 空间关系，以及研究更有效的训练策略。

**解读**:  
- **3D 空间关系**: 指处理三维空间中的物体关系，需更复杂的绘图操作。  
- **更有效的训练策略**: 如优化数据生成或减少计算资源需求。

---

### 总结

实验部分详细描述了 VILASR 的评估设置、主要结果、消融研究和推理时间扩展分析。VILASR 在五个空间推理基准（Maze、SpatialEval-Real、VSI-Bench、SPAR-Bench、MMSI-Bench）上表现出色，平均提升 18.4%，尤其在迷宫导航和视频推理任务中表现突出。消融研究表明，冷启动训练奠定基础，反思性拒绝采样增强自我纠错能力，强化学习优化推理效率。推理时间扩展分析显示三阶段训练逐步提升模型能力，强化学习有效缩小单次和多次尝试性能差距。结论强调了“绘图推理”范式的创新性，并提出未来扩展到 3D 空间和更高效训练的方向。