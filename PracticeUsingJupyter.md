# 🧪 Practice Programming in Jupyter Notebook

Let’s get familiar with **Jupyter Notebook**, our coding environment used for machine learning!

Jupyter Notebook is an **interactive programming tool** that allows you to write and run Python code in sections called **cells**. This makes it a great environment for experimenting with **AI applications**, **machine learning**, and **data analysis**.

---

## 🚀 Getting Started

**Good news!** Jupyter Notebook is already set up for you in the classroom below. You don’t need to download anything. Just follow the steps below:

---

## 🧭 Step 1: Navigate the Jupyter Notebook

### 🗂️ Workspace Overview:
- Locate the **Jupyter Notebook workspace**.
- Inside the notebook, you'll see **cells** where you can write and execute Python code.

### ⚙️ Basic Controls:
- **Running a Cell**:  
  Click inside a cell, then press **Run** (in the menu bar) to execute the code.

- **Adding New Cells**:  
  Click `Insert → Insert Cell Below` to add a new code cell.

- **Stopping Execution**:  
  If your code gets stuck, click `Kernel → Interrupt Kernel`.

- **Restarting the Notebook**:  
  To reset everything and run all cells again, go to `Kernel → Restart & Run All`.

- **Saving Your Work**:  
  Click `File → Save and Checkpoint` to save your progress.

---

## 💬 Let's Build a Chatbot!

As a practice activity, you'll build a simple **Tech Gadget Customer Support Chatbot** using Python.

Ready? Let’s get coding in the next cells!

---

# 💬 Exercise: Create a Tech Gadget Customer Support Chatbot

Imagine you own an online store that sells various **tech gadgets**.  
Customers frequently ask about:

- Product details  
- Return policies  
- Shipping options  
- Technical troubleshooting  

Instead of handling every question manually, let's build a **simple chatbot** that provides quick, automated responses.

---

## 🧠 What Your Chatbot Will Handle

### 🛍️ Product Information  
- “Tell me about product X”  
- “Do you have smartwatches?”

### 🚚 Shipping Details  
- “How long does shipping take?”  
- “What shipping methods are available?”

### 🔁 Return Policy  
- “What is your return policy?”  
- “How do I return a product?”

### 🛠️ Technical Support  
- “My gadget won’t turn on”  
- “How do I reset my device?”

---


# 🤖 Set Up Your Notebook: Tech Gadget Customer Support Chatbot

Let’s create a simple **Customer Support Chatbot** using Python in Jupyter Notebook!

---

## 🛠️ Step 1: Copy and Paste the Code

Click inside the first code cell of your Jupyter Notebook and paste the code below:

```python
# Simple Customer Support Chatbot

responses = {
    "hi": "Hello! Welcome to TechGadget Support. How can I assist you today?",
    "do you have smartwatches": "Yes, we have a variety of smartwatches. You can check them out on our products page.",
    "shipping time": "Shipping usually takes 3-5 business days.",
    "shipping methods": "We offer standard, expedited, and overnight shipping.",
    "return policy": "You can return products within 30 days of receipt for a full refund.",
    "how to return": "To return a product, please visit our returns page for a step-by-step guide.",
    "won’t turn on": "Make sure your gadget is charged. If it still won’t turn on, you can visit our troubleshooting page.",
    "reset device": "To reset your device, hold down the power button for 10 seconds. If that doesn't work, please check the manual for a factory reset.",
    "bye": "Thank you for visiting TechGadget. If you have more questions, feel free to ask. Goodbye!"
}

def get_bot_response(user_input):
    user_input = user_input.lower()

    for keyword, response in responses.items():
        if keyword in user_input:
            return response

    return "I'm not sure how to respond to that. Can you try asking something else?"

while True:
    user_input = input("You: ")
    if user_input.lower() in ["quit", "exit", "bye"]:
        print("Bot: Goodbye! If you have any more questions, we're here to help.")
        break

    response = get_bot_response(user_input)
    print(f"Bot: {response}")
```

---

## ▶️ Run Your Chatbot

1. **Click** inside the cell containing the chatbot code.  
2. **Press Run** in the menu bar to execute the chatbot.  
3. **Type in different customer questions** to see how the chatbot responds.  
4. To exit the chatbot, type `"bye"` or `"exit"`.

---

## 🎉 What You’ve Learned

✅ You navigated **Jupyter Notebook**.  
✅ You wrote and executed your **first chatbot program**.  
✅ You interacted with the chatbot to see how it processes customer questions.

---

Now you’re ready to explore **more advanced machine learning concepts** in Jupyter Notebook using **Python**! 🚀
