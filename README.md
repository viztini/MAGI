
---

# **MAGI**

MAGI is a simulation of the three-part supercomputer system from *Neon Genesis Evangelion*.
It models the MELCHIOR • 1, BALTHASAR • 2, and CASPER • 3 subsystems, each representing a different aspect of Dr. Naoko Akagi’s personality:

* **MELCHIOR • 1** — her as a scientist
* **BALTHASAR • 2** — her as a mother
* **CASPER • 3** — her as a woman

Each agent answers the question independently, and the final MAGI decision is determined through a voting process.

<p align="center">
  <img src="https://raw.githubusercontent.com/TomaszRewak/MAGI/master/examples/example_1.gif" width=800/>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/TomaszRewak/MAGI/master/examples/example_2.gif" width=800/>
</p>

---

## **Implementation**

This version of MAGI uses **OpenAI’s `gpt-4.1-mini` model**, replacing the original (now deprecated) ChatGPT-3.5 model.

The answering procedure is as follows:

1. The question is classified to determine if it can be answered with a yes/no response.
2. The original question is presented to each MAGI agent.
3. For yes/no questions, each agent classifies their answer into **yes**, **no**, or **conditional yes**.

Possible outcomes (evaluated in this order):

* **error (誤 差)** — at least one agent encountered an error
* **info (情 報)** — the question is not yes/no
* **no (拒 絶)** — at least one agent answered *no*
* **conditional (状 態)** — at least one agent gave a conditional yes
* **yes (合 意)** — all three agents gave an unconditional yes

Each agent can be inspected individually.

### **Agent Personalities (Prompts)**

* **MELCHIOR • 1** — scientist; seeks understanding and advancement
* **BALTHASAR • 2** — mother; seeks protection and wellbeing
* **CASPER • 3** — woman; seeks love, dreams, and desires

---

# **Usage**

You need **git** and **Python 3** installed.

Instructions for **Windows and Linux** are provided below.

---

## **1. Clone the repository**

```bash
git clone https://github.com/<your-username>/<your-fork>.git
cd MAGI
```

---

## **2. Create a Python virtual environment**

### **Windows**

```powershell
python -m venv .venv
.\.venv\Scripts\activate
```

### **Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## **3. Install dependencies**

```bash
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
```

---

## **4. Start the app**

```bash
python main.py
```

Then open:

```
http://127.0.0.1:8050/
```

---

## **5. Provide an API key**

Either paste your **OpenAI API key** into the **Access Code** field in the UI
—or— set an environment variable before launching:

### **Windows**

```powershell
setx OPENAI_API_KEY "your_api_key_here"
```

### **Linux**

```bash
export OPENAI_API_KEY="your_api_key_here"
```

---

## **6. Ask a question**

* Enter your question and press **Enter**
* Click on any subsystem to view the individual agent responses

---

## **Notes on this Fork**

This version includes **small but useful improvements**:

* Updated to OpenAI’s modern `gpt-4.1-mini` model
* Fixed compatibility issues with Python 3.12
* Improved Linux + Windows setup instructions
* Minor reliability fixes

The core logic and original design remain unchanged.

---

