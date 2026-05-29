# Learning Session Artifact Templates

Use these templates when the user wants an ongoing learning workspace.

Language-specific naming is mandatory:

- Chinese mode: generated learning artifacts use Chinese folder and file names.
- English mode: generated learning artifacts use English folder and file names.
- Repository/skill functional files keep required names: `SKILL.md`, `README*.md`, `LICENSE`, `agents/openai.yaml`, and `references/*.md`.
- Technical terms such as MDP, Q-Learning, PPO, DQN, and Bellman equation stay in English in both modes.

---

## Workspace Directory Structure

### Chinese Mode

```text
学习/<主题>/
├── 元数据/
│   ├── 学习档案.md          # 学习背景、目标、语言选择
│   ├── 学习进度.md          # 当前课程、测验结果、薄弱点
│   └── 错题记录.md          # 误区与纠正
├── 第01课-全局地图/
│   └── 课件.html            # 全局地图 + 嵌入式掌握检查
├── 第02课-MDP详解/
│   └── 课件.html            # 交互式课件 + 嵌入式测验
├── 第03课-价值函数/
│   └── 课件.html
└── ...
```

### English Mode

```text
learning/<topic-slug>/
├── _meta/
│   ├── profile.md          # Learner background, goal, language choice
│   ├── progress.md         # Current module, quiz results, weak spots
│   └── mistakes.md         # Misconceptions and corrections
├── lesson-01-<slug>/
│   └── index.html          # Global map + embedded mastery check
├── lesson-02-<slug>/
│   └── index.html          # Interactive lesson + embedded quiz
├── lesson-03-<slug>/
│   └── index.html
└── ...
```

**Naming examples by language:**

| Mode | Workspace | Lesson folder | Lesson HTML | Mastery Check |
|------|-----------|--------------|-------------|---------------|
| Chinese | `学习/强化学习/` | `第01课-全局地图/` | `课件.html` | embedded |
| Chinese | `学习/强化学习/` | `第02课-MDP详解/` | `课件.html` | embedded |
| English | `learning/reinforcement-learning/` | `lesson-01-global-map/` | `index.html` | embedded |
| English | `learning/reinforcement-learning/` | `lesson-02-mdp/` | `index.html` | embedded |

---

## Profile File

Chinese mode path: `元数据/学习档案.md`
English mode path: `_meta/profile.md`

```markdown
# Learner Profile / 学习者档案

- **Language / 语言**: [Chinese / English]
- **Domain / 目标领域**: [topic]
- **Background / 背景**: [what they already know]
- **Goal / 目标**: [project / interview / interest / exam / paper]
- **Deadline / 时间规划**: [if any]
- **Preferred Style / 讲解风格**: [detailed / concise, interactive HTML]
- **Success Criteria / 成功标准**: [what "done" looks like]
```

---

## Progress File

Chinese mode path: `元数据/学习进度.md`
English mode path: `_meta/progress.md`

```markdown
# Progress / 进度追踪

- Current / 当前进度: **Lesson X — [name]**
- Completed / 已完成:
  - Lesson 1 ✅
  - ...
- Weak spots / 薄弱点: [concepts to revisit]
- Next / 下一步: [specific action + command to type]
```

---

## Mistake Log

Chinese mode path: `元数据/错题记录.md`
English mode path: `_meta/mistakes.md`

```markdown
# Mistake Log / 错题记录

| Date | Concept | Mistake / 错误理解 | Corrected / 正确理解 | Retest? |
|------|---------|-------------------|---------------------|---------|
| ... | ... | ... | ... | ... |
```

---

## Lesson 1 Global Map HTML

Chinese mode path: `第01课-全局地图/课件.html`
English mode path: `lesson-01-global-map/index.html`

Lesson 1 is not a Markdown note. It is the first interactive HTML lesson and MUST include:

- a one-sentence field definition
- a comparison table against adjacent paradigms or fields
- 5-9 module cards that form the domain map
- a visible learning path/dependency diagram
- a glossary/term quick-reference section
- beginner traps and what to ignore at first
- embedded mastery check questions in the same page
- end-of-lesson self-check checklist and next-step command

---

## Interactive HTML Lesson Scaffold

For every lesson, including Lesson 1, generate an interactive HTML page. Below is the **minimum required scaffold**. Every HTML lesson must include all marked [REQUIRED] elements.

### Required CSS Variables (Dark Theme)

```css
:root {
  --bg: #0f172a;
  --card: #1e293b;
  --border: #334155;
  --text: #e2e8f0;
  --muted: #94a3b8;
  --accent: #38bdf8;
  --accent2: #a78bfa;
  --correct: #4ade80;
  --warn: #fbbf24;
  --danger: #f87171;
}
```

### Required HTML Structure

```html
<!DOCTYPE html>
<html lang="zh-CN">  <!-- or "en" -->
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lesson N: [Title] — [Domain]</title>
  <style>/* CSS here */</style>
</head>
<body>

  <!-- [REQUIRED] Sticky top bar -->
  <div class="topbar">
    <div class="breadcrumb">[Domain] / <span>Lesson N</span></div>
    <h1>[Lesson Title]</h1>
    <button onclick="resetAll()">[Reset Text]</button>
  </div>

  <!-- [REQUIRED] Sidebar TOC (hidden on screens < 1300px) -->
  <nav class="toc" id="toc">
    <a href="#s0">0. [Core Question]</a>
    <a href="#s1">1. [Section]</a>
    <!-- ... -->
  </nav>

  <div class="main">

    <!-- [REQUIRED] Section 0: Core question this lesson answers -->
    <div class="section" id="s0">
      <h2>[Icon] Core Question / 本课核心问题</h2>
      <p class="subtitle">[One-line summary]</p>
      <div class="def-box">
        <strong>Core Question:</strong> [The one question this lesson answers]
      </div>
    </div>

    <!-- Content sections with .section cards -->
    <div class="section" id="s1">
      <h2>[Icon] [Section Title]</h2>
      <p class="subtitle">[Subtitle]</p>
      <!-- content -->
    </div>

    <!-- ... more sections ... -->

    <!-- [REQUIRED] Final section: Mastery check -->
    <div class="section" id="sN" style="border-color: var(--accent2);">
      <h2>[Check Icon] Lesson N [Mastery Check / 掌握检查]</h2>
      <p class="subtitle">[N questions, pass to proceed]</p>
      <!-- mini-quiz blocks -->
    </div>

    <!-- [REQUIRED] End-of-lesson card -->
    <div class="section end-card" id="endCard">
      <h3>[Completion Heading]</h3>
      <p>[Summary message]</p>

      <!-- [REQUIRED] Self-check checklist -->
      <div class="checklist">
        <span class="check-item" onclick="toggleCheck(this)">☐ [Check item 1]</span>
        <span class="check-item" onclick="toggleCheck(this)">☐ [Check item 2]</span>
        <!-- ... -->
      </div>

      <!-- [REQUIRED] Next-step command -->
      <div class="next-step">
        <p>[Prompt text]</p>
        <span class="next-cmd">[Command to type in Claude Code]</span>
        <p class="preview">[Next lesson preview]</p>
      </div>
    </div>

  </div><!-- /main -->

  <!-- [REQUIRED] Floating bottom bar -->
  <div class="bottom-bar" id="bottomBar">
    <span class="msg">[Completion message]</span>
    <span>[Next step]: <code>[command]</code></span>
    <button onclick="document.getElementById('endCard').scrollIntoView({behavior:'smooth'})">[View Card]</button>
  </div>

  <script>
  // [REQUIRED] All functions below must be present

  // Scroll to detail element with sticky header offset
  function scrollToDetail(id) {
    var el = document.getElementById(id);
    if (!el) return;
    var top = el.getBoundingClientRect().top + window.pageYOffset - 85;
    window.scrollTo({ top: top, behavior: "smooth" });
  }

  // Toggle accordion open/close
  function toggleAccordion(id) {
    document.getElementById(id).classList.toggle("open");
  }

  // Switch perspective tab (query panels from parent SECTION, not tabs container)
  function switchTab(name) {
    var section = document.getElementById("sN"); // section containing the tabs
    section.querySelectorAll(".tab-btn").forEach(function(b) { b.classList.remove("active"); });
    section.querySelectorAll(".tab-panel").forEach(function(p) { p.classList.remove("active"); });
    var btnMap = { user: 0, biz: 1, eng: 2 };
    section.querySelectorAll(".tab-btn")[btnMap[name]].classList.add("active");
    document.getElementById("tab-" + name).classList.add("active");
  }

  // Mini-quiz answer handler (guards against double-click)
  var _mqAnswered = {};
  function checkMQ(mqId, optIdx, isCorrect) {
    if (_mqAnswered[mqId]) return;
    _mqAnswered[mqId] = true;
    var mq = document.getElementById(mqId);
    var explain = document.getElementById(mqId + "-explain");
    var opts = mq.querySelectorAll(".opt");
    opts.forEach(function(o) { o.classList.remove("chosen-correct", "chosen-wrong"); });
    if (isCorrect) {
      opts[optIdx].classList.add("chosen-correct");
      explain.className = "explain show ok";
      explain.innerHTML = "[Correct icon] <strong>[Correct!]</strong> " + explain.innerHTML;
    } else {
      opts[optIdx].classList.add("chosen-wrong");
      explain.className = "explain show no";
      explain.innerHTML = "[Wrong explanation text]";
    }
  }

  // Self-check checklist toggle
  function toggleCheck(el) {
    if (el.classList.contains("done")) {
      el.classList.remove("done");
      el.textContent = el.textContent.replace("☑", "☐");
    } else {
      el.classList.add("done");
      el.textContent = el.textContent.replace("☐", "☑");
    }
  }

  // Reset all interactive state
  function resetAll() {
    _mqAnswered = {};
    document.querySelectorAll(".accordion").forEach(function(a) {
      if (a.id !== "accWhy") a.classList.remove("open");
    });
    document.querySelectorAll(".mini-quiz .explain").forEach(function(e) {
      e.classList.remove("show", "ok", "no");
    });
    document.querySelectorAll(".mini-quiz .opt").forEach(function(o) {
      o.classList.remove("chosen-correct", "chosen-wrong");
    });
    document.querySelectorAll(".check-item").forEach(function(c) {
      c.classList.remove("done");
      if (c.textContent.indexOf("☑") !== -1) c.textContent = c.textContent.replace("☑", "☐");
    });
    // Reset tabs to first
    var section = document.getElementById("sN");
    if (section) {
      section.querySelectorAll(".tab-btn").forEach(function(b) { b.classList.remove("active"); });
      section.querySelectorAll(".tab-panel").forEach(function(p) { p.classList.remove("active"); });
      if (section.querySelectorAll(".tab-btn")[0]) section.querySelectorAll(".tab-btn")[0].classList.add("active");
      if (section.querySelectorAll(".tab-panel")[0]) section.querySelectorAll(".tab-panel")[0].classList.add("active");
    }
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  // [REQUIRED] IntersectionObserver for floating bottom bar
  (function() {
    var bottomBar = document.getElementById("bottomBar");
    var endCard = document.getElementById("endCard");
    var shown = false;
    var observer = new IntersectionObserver(function(entries) {
      if (entries[0].isIntersecting && !shown) {
        bottomBar.classList.add("visible");
      }
    }, { threshold: 0.3 });
    observer.observe(endCard);
    bottomBar.addEventListener("click", function(e) {
      if (e.target.tagName === "BUTTON") return;
      bottomBar.classList.remove("visible");
      shown = true;
    });
  })();
  </script>
</body>
</html>
```

### Required CSS Classes Summary

| Class | Purpose |
|-------|---------|
| `.topbar` | Sticky header with breadcrumb, title, reset button |
| `.toc` | Fixed sidebar TOC (hidden < 1300px) |
| `.section` | Content card with rounded corners, margin-bottom |
| `.def-box` | Left-bordered definition block (blue accent) |
| `.example-box` | Left-bordered example block (green accent) |
| `.tag-def`, `.tag-eg`, `.tag-warn` | Inline label badges |
| `.accordion`, `.accordion-header`, `.accordion-body` | Collapsible FAQ |
| `.mdp-tuple`, `.mdp-item` | Clickable concept cards |
| `.tabs`, `.tab-btn`, `.tab-panel` | Perspective switcher |
| `.mini-quiz`, `.opt`, `.explain` | Embedded quiz with feedback |
| `.formula` | Centered equation display |
| `.loop-diagram`, `.loop-node`, `.loop-arrow` | Agent-Environment flow |
| `.end-card` | Dashed-border completion card |
| `.checklist`, `.check-item`, `.check-item.done` | Self-assessment checklist |
| `.next-cmd` | Monospace code block for next command |
| `.bottom-bar` | Floating slide-up bar on scroll-to-end |
| `.annotate`, `.annotate .tooltip` | Hover annotation tooltips |

---

## Embedded Mastery Check

Every lesson page includes its mastery check inside the same HTML file. Do not generate standalone quiz files by default.

Required behavior:

- 2-4 questions per lesson
- auto-grading with instant feedback (correct / partially-correct / wrong)
- hint button per question where useful
- sample answer or explanation after the learner answers
- completion state that shows the next-step command

Language: all UI text in the learner's chosen language. Technical terms in English.
