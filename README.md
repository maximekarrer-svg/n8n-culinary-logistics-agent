
# Culinary Logistics Agent 

## 📋 Project Overview

This project was developed as part of an AI formation at **ESCP Business School**. The objective was to build a functional AI agent using **n8n** to solve a real-world personal or professional problem.

This agent automates the entire lifecycle of meal planning:

1. **Content Generation**: Creating full recipes from a simple dish name.
2. **Data Logging**: Storing recipe details and instructions in a structured database.
3. **Logistics Optimization**: Aggregating ingredients from multiple recipes, calculating total quantities, and generating a consolidated, deduplicated grocery list.

---

## 🛠️ Technical Architecture

The workflow follows a sophisticated data pipeline to ensure accuracy and scalability:

* **Trigger**: Manual or scheduled start.
* **Data Retrieval**: Fetches selected dishes from a Google Sheets document.
* **Agent 1 (Creative Chef)**: Uses the **Gemini 2.0 Flash** model to generate ingredients and cooking steps.
* **Aggregation**: A dedicated **Aggregate Items** node compiles all recipe data into a single batch.
* **Agent 2 (Logistics Optimizer)**: Processes the batch to sum up quantities (e.g., merging 500g + 1kg into 1.5kg) and outputs a structured JSON array.
* **Parsing (JavaScript)**: A custom **Code Node** sanitizes the AI output (removing Markdown artifacts) and converts it into individual items.
* **Final Delivery**: Appends the optimized list to a Google Sheets "Grocery List" tab.

---

## 🚀 How to Use

1. **Prerequisites**: An n8n instance and a Google Sheets account.
2. **Import**: Download the `grocery_agent_workflow.json` file from this repository.
3. **Setup**: Import the JSON into n8n and update the Google Sheets credentials.
4. **Execution**: Run the workflow to transform your recipe names into a perfectly calculated grocery list.

---

## 🧠 Key Learnings

* **Data Sanitation**: Learned how to handle LLM "hallucinations" or formatting errors (like unwanted Markdown tags) using JavaScript within n8n.
* **Token Efficiency**: Optimized the process by using an aggregation node, ensuring the logistical AI only runs once for the entire batch rather than per item.
* **Hybrid Systems**: Combined the creative capabilities of LLMs with the rigid requirements of structured databases (Google Sheets).

---

### 👨‍🎓 Author

**Maxime Karrer**
 AI for Business Program.

---
