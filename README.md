# Shopie Guide 🛍️🤖

> An AI-powered e-commerce product discovery and recommendation assistant built with Botpress and deployed on GitHub Pages.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-22272e?style=for-the-badge)](https://ashishsrs01.github.io/Mini-E-commerce-guide-chatbot/)
[![Botpress](https://img.shields.io/badge/AI-Botpress-167d88?style=for-the-badge)](https://botpress.com/)
[![Frontend](https://img.shields.io/badge/Frontend-HTML%2FCSS%2FJS-e34f26?style=for-the-badge)](https://developer.mozilla.org/en-US/docs/Web)
[![Hosting](https://img.shields.io/badge/Hosting-GitHub%20Pages-24292f?style=for-the-badge)](https://pages.github.com/)

## 🔗 Live Demo

**Try Shopie Guide:**  
https://ashishsrs01.github.io/Mini-E-commerce-guide-chatbot/

Use the **Chat with Shopie Guide** button to start a conversation with the AI product advisor.

---

## 📌 Overview

**Shopie Guide** is a conversational AI assistant built to help users discover and compare products through natural language.

Instead of navigating a rigid sequence of category and budget buttons, users can simply describe what they need:

> "I need a gaming laptop under ₹80,000."

> "Show me Samsung phones under ₹50,000."

> "I need running shoes under ₹10,000."

> "Compare two phones under ₹40,000."

Shopie Guide searches a structured product catalog, applies the user's requirements, and returns relevant recommendations with product details and reasoning.

### Core pipeline

**Natural Language → Retrieval → Filtering → Ranking → Explanation**

---

## ✨ Features

### 🤖 Conversational Product Discovery

Users can describe their shopping requirements naturally rather than following a fixed chatbot flow.

### 💰 Budget-Aware Recommendations

The assistant understands expressions such as:

- Under ₹30,000
- 30k
- Around ₹50,000
- Between ₹40,000 and ₹60,000

Budget is treated as an important recommendation constraint.

### 🎯 Requirement-Aware Ranking

The user's primary use case influences the recommendation ranking.

Examples:

- Gaming → prioritize gaming-oriented laptops
- Running → prioritize running shoes
- Photography → prioritize relevant camera-oriented phones
- College + coding → prioritize suitable laptops for those requirements

### 🔎 Catalog-Grounded Answers

Product information is retrieved from the connected ProductCatalog instead of being invented by the assistant.

### ⚖️ Product Comparison

Users can compare products using factors such as:

- Price
- Rating
- Specifications
- Intended use
- Overall fit for their requirements

### 💬 Context-Aware Follow-Ups

Shopie Guide understands follow-up requests such as:

- "Tell me more about the first one."
- "Compare the first two."
- "Is there a cheaper option?"
- "Which one do you recommend?"

### 🛡️ Transparent Data Boundaries

The catalog is an indicative demonstration dataset, not live marketplace inventory. Shopie Guide does not claim live Amazon, Flipkart, or other marketplace pricing or availability.

---

## 🛍️ Supported Categories

| Category | What Shopie Guide Can Help With |
|---|---|
| 📱 Phones | Budget, brand, camera, performance, everyday use |
| 💻 Laptops | Gaming, coding, college, productivity, general use |
| 👟 Shoes | Running, daily use, comfort, sport |

---

## 📊 Product Catalog

The current Shopie Guide catalog contains approximately **490 product entries** across the three supported categories.

The structured data includes fields such as:

- Product ID
- Category
- Brand
- Model
- Variant
- Color
- Price
- Rating
- Review count
- Stock status
- Best-for / use case
- Key specifications
- Warranty
- Data note

The catalog is imported into **Botpress Tables** and connected to the **Knowledge Base**, allowing the Autonomous Node to retrieve product information through natural-language requests.

> **Important:** The catalog is intended for demonstration purposes. Its prices, ratings, reviews, stock status, and availability should not be treated as live marketplace information.

---

## 🧠 Architecture

~~~text
                    ┌─────────────────────┐
                    │       User          │
                    │ Natural-language    │
                    │      request        │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Botpress Autonomous │
                    │        Node         │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Knowledge Base    │
                    │      Search         │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   ProductCatalog    │
                    │   Botpress Table    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Filter + Requirement│
                    │  aware ranking      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Recommendation +    │
                    │      Explanation    │
                    └─────────────────────┘
~~~

---

## ⚙️ How It Works

A request such as:

> "I need a phone under ₹30,000 for everyday use."

is processed as follows:

1. Identify the product category.
2. Extract the user's budget.
3. Understand the intended use.
4. Search the ProductCatalog.
5. Filter products using the requirements.
6. Rank the strongest matches.
7. Return product details and explain the recommendation.

The bot is instructed to prioritize the user's actual requirements rather than simply returning the highest-rated or cheapest item.

---

## 🧩 AI Design Principles

### Grounded Retrieval

Product-related responses are based on the connected ProductCatalog.

### No Fabrication

The assistant should not invent products, prices, specifications, ratings, reviews, warranties, availability, or purchase links.

### Requirement Priority

The primary use case is prioritized alongside budget, specifications, brand preference, ratings, and other constraints.

### Context Awareness

Follow-up questions use the current conversation context.

### Transparent Limitations

The assistant clearly distinguishes demonstration data from live marketplace information.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Conversational AI | **Botpress Cloud** |
| AI Agent | **Autonomous Node** |
| Knowledge | **Botpress Knowledge Base** |
| Structured Data | **Botpress Table / ProductCatalog** |
| Frontend | **HTML5 + CSS3 + JavaScript** |
| Webchat | **Botpress Webchat v3.7** |
| Hosting | **GitHub Pages** |
| Version Control | **Git + GitHub** |

---

## 📁 Repository Structure

~~~text
Mini-E-commerce-guide-chatbot/
│
├── index.html
│
├── data/
│   └── products.csv
│
└── README.md
~~~

### index.html

The public-facing Shopie Guide showcase website containing:

- Shopie Guide branding
- Product discovery landing page
- Supported categories
- Example shopping prompts
- Project architecture explanation
- Responsible-AI/data notes
- Botpress Webchat integration

### data/products.csv

Original/local sample product data retained in the repository.

The current conversational demo uses the **ProductCatalog configured in Botpress** as its primary product knowledge source.

---

## 🚀 Deployment

The website is deployed as a static site through GitHub Pages.

~~~text
GitHub Repository
       │
       ▼
   index.html
       │
       ▼
 GitHub Pages
       │
       ▼
Shopie Guide Website
       │
       ▼
 Botpress Webchat
       │
       ▼
 Shopie Guide Agent
~~~

The website provides the public interface, while the conversational AI and product knowledge are handled through Botpress.

---

## 🧪 Example Prompts

Try these in the live demo:

**Budget**

> I need a phone under ₹30,000.

**Gaming**

> Recommend a gaming laptop under ₹80,000.

**Brand**

> Show me Samsung phones under ₹50,000.

**Running**

> I need running shoes under ₹10,000.

**Comparison**

> Compare two phones under ₹40,000.

**Multiple requirements**

> I need a laptop for college and coding under ₹70,000.

**Conversation context**

> Tell me more about the first product.

---

## ⚠️ Limitations

Shopie Guide is a demonstration project and is not connected to a live e-commerce marketplace API.

Therefore:

- Prices are indicative.
- Ratings are indicative.
- Review counts are indicative.
- Stock information is not guaranteed to be live.
- Availability is not guaranteed.
- The assistant cannot place orders.
- The assistant cannot process payments.
- The assistant cannot guarantee marketplace availability.
- Purchase links should not be assumed to be verified.

These limitations are intentionally communicated by the assistant.

---

## 🎯 Project Goal

The project demonstrates how conversational AI can make e-commerce product discovery more flexible by combining:

**Natural Language + Structured Data + Retrieval + Recommendation Logic**

The current version moves beyond a simple fixed-flow chatbot by allowing users to express more flexible shopping requirements and receive catalog-grounded recommendations.

---

## 🔮 Future Improvements

Potential future iterations include:

- Live product APIs for real-time pricing and availability
- Verified marketplace links
- Additional product categories
- Personalized user preference profiles
- Recommendation feedback and preference learning
- More advanced product ranking
- Semantic similarity-based recommendations
- Shopping analytics
- Multilingual support
- User accounts and saved recommendations

---

## 👨‍💻 Author

**Ashish Sharma**  
AI & Data Science Student

**GitHub:**  
https://github.com/ashishsrs01

**Project Repository:**  
https://github.com/ashishsrs01/Mini-E-commerce-guide-chatbot

---

## 📜 Project Evolution

This project originally started as a low-code e-commerce chatbot exercise using a fixed conversational flow and WotNot.

It has since been redesigned as **Shopie Guide** using:

- Botpress Cloud
- Autonomous Node
- Knowledge Base
- Structured ProductCatalog
- Requirement-aware recommendation behavior
- Botpress Webchat
- A redesigned GitHub Pages showcase

This evolution demonstrates the transition from a basic fixed-flow chatbot to a more flexible, knowledge-grounded conversational product assistant.

---

## ⭐ Try It

**Live Demo:**  
https://ashishsrs01.github.io/Mini-E-commerce-guide-chatbot/

**Repository:**  
https://github.com/ashishsrs01/Mini-E-commerce-guide-chatbot

<p align="center">
  Built with 🤖 AI, structured data, and thoughtful recommendation logic.
</p>
