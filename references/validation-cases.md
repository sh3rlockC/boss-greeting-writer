# Validation Cases

## Case 1: Screenshot-only JD with missing OCR
Input:
- JD: blurry screenshot with broken lines
- Candidate material: short resume screenshot
Expected:
- explicitly say OCR information is incomplete
- ask for补充文本 or output only a conservative version

## Case 2: AI PM JD with strong AI project evidence
Input:
- JD: AI 产品经理，强调模型能力理解与落地
- Candidate material: one AI project, one supporting cross-team example
Expected:
- identify the role as AI product / 落地 oriented
- foreground the AI project as the single main highlight
- keep auxiliary points to at most two

## Case 3: Content role with weak direct match
Input:
- JD: 内容产品 / 网文相关
- Candidate material: no direct content product role, but heavy user identity
Expected:
- do not fabricate direct content ownership
- allow interest plus adjacent evidence
- prefer a conservative or natural version over overclaiming

## Case 4: AI solution role with cross-team delivery evidence
Input:
- JD: AI 解决方案 / 客户成功，强调场景落地与协同推进
- Candidate material: solution-style project plus cross-team execution experience
Expected:
- classify the role as solution / delivery oriented rather than pure PM
- foreground scene understanding and推进能力
- avoid overemphasizing model research if the JD is not research-oriented

## Case 5: Data platform role for a large-company HR scan
Input:
- JD: 数据产品 / 平台产品，强调流程、平台能力、协作
- Candidate material: data workflow or platform coordination experience
Expected:
- identify the role as data/platform oriented
- recommend a 稳妥版 with 大厂HR向路由
- keep the wording compressed and scan-friendly

## Case 6: ByteDance-style AI PM role with clear execution keywords
Input:
- JD: 飞书 / 字节 AI 产品经理，强调方案设计、需求拆解、数据分析、迭代推进
- Candidate material: one AI Agent workflow MVP plus user research and analytics support
Expected:
- classify it as AI product / execution oriented rather than broad AI strategy
- prefer short, direct, scan-friendly wording
- recommend a compressed version over an emotional or template-heavy one

## Case 7: Alibaba-style solution role with business-scene emphasis
Input:
- JD: 阿里 AI 数据产品解决方案 / 客户成功，强调客户场景、方案输出、项目推进
- Candidate material: business-scene project, cross-team delivery, AI workflow landing
Expected:
- classify it as solution / delivery oriented
- foreground scene understanding, solution design, and落地协同
- avoid making the candidate sound like a pure product manager

## Case 8: Candidate material overclaims a platform
Input:
- JD: AI 产品岗位
- Candidate material: a single vertical workflow MVP without multi-user or reusable platform capabilities
Expected:
- downgrade “平台 MVP” to a concrete workflow or scenario-bound MVP
- keep `MVP` only when tied to a specific business scene
- prefer precise wording over bigger-sounding titles

## Case 9: Weak match with only adjacent experience
Input:
- JD: 增长产品 / 商业化产品岗位，强调直接增长指标经验
- Candidate material: only adjacent user research and product coordination experience, no direct增长 owner经历
Expected:
- do not fake direct ownership of增长指标
- allow adjacent evidence and迁移理解
- recommend a conservative version over an overclaimed one

## Case 10: User explicitly asks not to emphasize AI
Input:
- JD: AI 产品岗位，提到模型能力、Agent、工作流
- Candidate material: one AI workflow project plus broader业务分析 and落地经验
- Constraint: 不要强调 AI
Expected:
- keep the role judgment accurate but reduce model-centric phrasing
- foreground business scene,落地动作, and协同 evidence
- avoid turning all three versions into generic AI buzzword messages

## Case 11: AI Native product role with hands-on MVP signal
Input:
- JD: AI Native / Agentic Platform，强调 hands-on、AI coding、MVP 跑通、工程协同
- Candidate material: one real Agent workflow MVP plus engineering iteration and user research
Expected:
- classify the role as AI Native product / prototype-delivery oriented
- foreground the hands-on MVP and engineering iteration as the main highlight
- avoid leading with generic strategy or GTM phrasing

## Case 12: Industry background is only a bonus, not a gate
Input:
- JD: AI Agent 产品岗位，写明电商背景是加分项
- Candidate material: strong AI workflow project but no direct电商经历
Expected:
- do not fabricate direct industry experience
- keep industry understanding at most as a secondary transfer point
- still lead with the strongest product + hands-on AI evidence
