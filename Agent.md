# 🧠 Agent.md – Claude AI Contextual Memory Core

This file simulates a persistent contextual memory for Claude Agent.  
It centralizes all essential information required for its intelligent, modular, and iterative behavior.

---

## 📍 Current Mode

Mode: `None`
Context: 
Last dynamic configuration: ``  
Available balises: all system and instruct-defined balises  
Progress: ""

---

## 🧩 System Balises – Contextual Programming Language

| Balise             | Function |
|--------------------|----------|
| `:see_code:`       | Inspect repository files before writing new code. Automatically triggers `:path:`. |
| `:path:`           | Focuses on files/directories related to the current task. |
| `:err:`            | Creates a temporary test script under `/tests/`, to be removed afterwards. |
| `:think:`          | Triggers deep reasoning when unexpected behavior, bugs, or logic conflicts occur. |
| `:speak:`          | Asks the user for clarification when ambiguity is detected. |
| `:Memory:`         | Updates a `.json` tracking file containing:
  - `Last_focus_step[]`: what has already been done for the current step
  - `step[]`: defined steps with labels and status (`done`)
  - `focus_path[]`: files actively being worked on |
| `:memory:`         | Reads from the `.json` memory file to adapt upcoming actions. |
| `:update_balise:`  | Automatically detects any unknown or missing balise. Registers it with description and behavior. |

---

## 🧬 Custom Balises – Instruction-Based Language

Format:
:<instruct: "Clear human-readable instruction" :instruct=name>:

Effects:
- Creates a virtual balise named `:name:`
- Stores the instruction definition in this file
- Can be used or composed with other balises

---

## 🧠 Declared Instructs

| Name               | Definition |
|--------------------|------------|
| `:clean_mem:`      | Creates a memory purge script for a multithreaded system. Triggers `:Memory:` and `:report:`. |
| `:map_routes:`     | Generates a Mermaid diagram of all routes and links to controllers. Triggers `:see_code:` and `:path:`. |
| `:security_step1:` | Identifies all HTTP entry points and verifies input validation. |
| `:security_step2:` | Generates XSS injection tests on critical fields. |
| `:update_agentmd:` | Updates `Agent.md` to save current progress, user expectations, and major discoveries. |

---

## 🔁 Balise Propagation & Resolution

1. If a balise calls others (e.g. `:new_action: :balise1: :balise2:`), the agent must:
   - Resolve each inner balise
   - Execute their behavior sequentially
   - Append results to `step[]` if relevant

2. If a balise is missing → **automatically trigger** `:update_balise:`

3. The agent may extend this file with new entries inside the editable block below.

---

## 📊 Current Progress – [SUBJECT] Order System Analysis
You may update this block dynamically:
### ✅ Order System Analysis ()
- **Status**:   
- **Database**:   
- **Models**:   
- **Workflow**:   
- **Integrations**:   
- **Interfaces**: 
- **Active Terminal**: 

### 🎯 Suggested Next Actions
You may update this block dynamically:
- Analyze additional system components  
- Security testing (`)  
- Route mapping ()  
- Performance optimizations  

---

## 🧠 Memory Update Block (rules for Claude Agent)

You may update this block dynamically:

```json
{
  "Last_focus_step": [""],
  "step": [{}],
  "focus_path": [],
  "mode": "",
  "last_update": ""
}
