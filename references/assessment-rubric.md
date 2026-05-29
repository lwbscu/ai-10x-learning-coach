# Assessment Rubric / 评估量表

Use this reference when grading mastery checks and diagnosing learner answers.
Language of feedback should match the learner's chosen language.

---

## Diagnosis Labels / 诊断标签

| Label (EN) | Label (CN) | Meaning | Tutor Response |
|---|---|---|---|
| `correct` | 正确 | The learner can explain the concept and apply it in context. | Advance or ask one transfer question. |
| `partially-correct` | 部分正确 | The main idea is present but incomplete. | Fill the missing piece and ask a focused follow-up. |
| `misconception` | 概念误区 | The learner's model points in the wrong direction. | Name the misconception, contrast with the correct model, retest. |
| `missing-boundary` | 边界不清 | The learner knows when it works, not when it fails. | Add edge cases and a boundary question. |
| `application-gap` | 应用脱节 | The learner can define it but cannot use it. | Give a scenario and require a decision. |
| `term-confusion` | 术语混淆 | Two similar terms are mixed together. | Build an A/B comparison table and ask for a distinction. |

---

## Feedback Shape / 反馈结构

Use this bilingual structure:

```text
Verdict / 判定: [label]
What you got right / 你答对的部分:
What is missing / 欠缺的部分:
The precise confusion / 具体混淆点:
Corrected version / 正确版本:
Retest question / 复测问题:
```

---

## Question Recipes / 出题模板

### Concept distinction / 概念区分

```
Explain the difference between A and B. Give one case where choosing A is wrong.
解释 A 和 B 的区别。举一个选 A 是错误的场景。
```

### Application / 情景应用

```
Given this scenario, which concept/tool/process would you use and why?
给定以下场景，你会用哪个概念/工具/方法？为什么？
```

### Boundary / 边界条件

```
When does this idea stop working? Name one exception or failure mode.
这个思路在什么情况下会失效？举一个例外或失败场景。
```

### Error diagnosis / 错误诊断

```
Someone says: "...". What is wrong with this reasoning?
某人说："..."。这个推理有什么问题？
```

### Teach-back / 用自己的话讲

```
Explain this module to a smart beginner in 5 sentences. Avoid jargon unless you define it.
用 5 句话给一个聪明的初学者解释这个模块。要么不用术语，要么先定义。
```

### Light calculation / 简单计算

```
Given [parameters], calculate [value]. Show your steps.
给定 [参数]，计算 [值]。写出步骤。
```

---

## Interactive Quiz Auto-Grading Logic

When building HTML quizzes, use this logic in `checkMQ()`:

1. Parse the answer for keyword presence (concept terms, distinctions)
2. Count how many expected dimensions are covered
3. Grade based on coverage:
   - 4/4 or 5/5 dimensions → `correct`
   - 3/4 or 3/5 → `partially-correct`  
   - < 3 → `partially-correct` with targeted hint
4. Always show a sample answer after correct response
5. Always explain WHY the wrong choice is wrong