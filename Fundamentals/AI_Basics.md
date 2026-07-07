````markdown
# AI Fundamentals: Prompt, Workflow, RAG, and AI Agents

> **Learning Objective**
>
> By the end of this guide, you will understand:
>
> - What is a Prompt?
> - What is a Workflow?
> - What is Retrieval-Augmented Generation (RAG)?
> - What is an AI Agent?
> - How are they related?
> - When should each be used?

---

# Table of Contents

1. Introduction
2. What is a Prompt?
3. What is a Workflow?
4. What is RAG?
5. What is an AI Agent?
6. Prompt vs Workflow
7. Workflow vs Agent
8. RAG vs Agent
9. Prompt vs Agent
10. Complete Comparison Table
11. Real-World Examples
12. Summary

---

# Introduction

Modern AI applications are built using several concepts that work together:

- Prompt
- Workflow
- Retrieval-Augmented Generation (RAG)
- AI Agent

These terms are often used interchangeably, but they represent different levels of capability.

Think of them as building blocks.

```
Prompt
    │
    ▼
Workflow
    │
    ▼
RAG Workflow
    │
    ▼
AI Agent
```

Each level adds more intelligence and automation.

---

# 1. What is a Prompt?

A **prompt** is simply the instruction given to a Large Language Model (LLM).

It tells the model what to do.

## Examples

### Example 1

```
Translate this paragraph into Tamil.
```

### Example 2

```
Write Python code to reverse a string.
```

### Example 3

```
Summarize this PDF.
```

The model processes the instruction and generates a response.

---

## Prompt Flow

```
User
   │
   ▼
Prompt
   │
   ▼
Large Language Model
   │
   ▼
Response
```

---

## Characteristics

- Single input
- Single output
- No planning
- No decision making
- No memory
- No external tool usage (unless enabled)

---

## Real-Life Analogy

Imagine asking a teacher:

> "What is Machine Learning?"

The teacher answers.

The conversation ends.

That is a prompt.

---

# 2. What is a Workflow?

A **workflow** is a predefined sequence of steps that accomplishes a task.

Unlike a prompt, multiple operations happen one after another.

---

## Example

Suppose a company receives resumes.

Workflow:

```
Receive Resume

↓

Extract Skills

↓

Compare with Job Description

↓

Calculate Match Score

↓

Send Result
```

Every candidate goes through the exact same sequence.

---

## Workflow Characteristics

- Fixed sequence
- Predictable
- Rule-based
- Repeatable
- Easy to automate

---

## Another Example

Customer Order Workflow

```
Customer Places Order

↓

Payment Verification

↓

Inventory Check

↓

Generate Invoice

↓

Ship Product

↓

Send Email
```

---

# Prompt vs Workflow

| Prompt | Workflow |
|---------|----------|
| One instruction | Multiple connected steps |
| One response | Many operations |
| No orchestration | Full orchestration |
| LLM only | APIs, databases, LLMs, services |

---

# 3. What is RAG?

## Retrieval-Augmented Generation

RAG is a workflow where the AI retrieves relevant information before generating an answer.

Instead of answering only from memory, the model first searches a knowledge base.

---

## Why RAG?

Large Language Models

- can hallucinate
- may not know recent information
- cannot access private company documents
- cannot answer organization-specific questions without additional context

RAG solves these problems.

---

## RAG Architecture

```
                User Question
                      │
                      ▼
             Embedding Model
                      │
                      ▼
             Vector Database
                      │
              Similarity Search
                      │
                      ▼
          Relevant Documents Retrieved
                      │
                      ▼
          Prompt + Retrieved Context
                      │
                      ▼
            Large Language Model
                      │
                      ▼
               Final Answer
```

---

## Step-by-Step RAG Flow

### Step 1

Collect documents

Examples

- PDFs
- Word files
- Web pages
- Emails
- Company wiki

---

### Step 2

Split documents into chunks.

```
Employee Handbook

Chunk 1

Introduction

Chunk 2

Leave Policy

Chunk 3

Medical Benefits

Chunk 4

Insurance
```

---

### Step 3

Convert each chunk into vectors.

```
Leave Policy

↓

[0.24, -0.56, 0.87, ...]
```

---

### Step 4

Store vectors inside a Vector Database.

Examples

- FAISS
- Chroma
- Pinecone
- Weaviate
- Milvus

---

### Step 5

User asks a question.

```
How many annual leaves do employees receive?
```

---

### Step 6

The same question is converted into a vector.

---

### Step 7

Similarity search retrieves the most relevant chunks.

---

### Step 8

The retrieved context is appended to the prompt.

```
Context

Employees receive 20 annual leaves.

Question

How many annual leaves do employees receive?
```

---

### Step 9

The LLM generates the answer.

```
Employees receive 20 annual leave days.
```

---

# RAG Workflow

```
Question

↓

Embedding

↓

Vector Search

↓

Retrieve Documents

↓

Add Context

↓

LLM

↓

Answer
```

---

## Advantages

- Current information
- Company knowledge
- Reduced hallucination
- Better factual accuracy
- No retraining required

---

# 4. What is an AI Agent?

An **AI Agent** is an intelligent software system that uses an LLM as its reasoning engine but can also plan,
remember, use tools, and perform actions to achieve a goal.

An agent is much more than a chatbot.

---

## Agent Components

```
               User Goal
                    │
                    ▼
                 AI Agent
                    │
     ┌──────────────┼───────────────┐
     │              │               │
     ▼              ▼               ▼
 Planner        Memory          Tool Manager
     │                              │
     ▼                              ▼
 Large Language Model         APIs / Database /
                              Search / Email /
                              Calendar / Python
                    │
                    ▼
             Decision Engine
                    │
                    ▼
               Final Result
```

---

## What Can an Agent Do?

An AI agent can

- Search the web
- Query databases
- Use company documents
- Execute Python code
- Send emails
- Schedule meetings
- Read PDFs
- Call APIs
- Make decisions
- Retry failed operations
- Plan multiple steps

---

## Example

User says

```
Book the cheapest flight to London next month.
```

The agent may

1. Search airline websites
2. Compare prices
3. Check baggage policy
4. Find cheapest option
5. Create itinerary
6. Email results

No predefined workflow is required.

The agent decides each step dynamically.

---

# Agent Decision Flow

```
User Goal

↓

Think

↓

Do I need more information?

↓

Yes

↓

Search

↓

Enough Information?

↓

No

↓

Search Again

↓

Enough Information?

↓

Yes

↓

Generate Answer

↓

Perform Action

↓

Finish
```

---

# Workflow vs Agent

Workflow

```
Start

↓

Step 1

↓

Step 2

↓

Step 3

↓

Finish
```

Everything is predefined.

---

Agent

```
Goal

↓

Think

↓

Search?

↓

Need API?

↓

Need Calculator?

↓

Need Database?

↓

Need Another Search?

↓

Finish
```

Every execution may follow a different path.

---

# RAG vs Agent

Many people confuse these concepts.

RAG retrieves information.

Agents make decisions.

Example

Question

```
What is Python?
```

Agent answers directly.

Question

```
What is our company's leave policy?
```

Agent realizes it needs company data.

↓

Uses RAG

↓

Retrieves documents

↓

Answers.

The agent decides **when** to use RAG.

---

# Prompt vs Agent

Prompt

```
Write Python code to sort numbers.
```

Response

```
Python Code
```

Done.

---

Agent

```
Create a Python project.

↓

Generate Code

↓

Run Tests

↓

Fix Errors

↓

Create README

↓

Push to GitHub

↓

Notify User
```

Much more autonomous.

---

# Complete Comparison

| Feature | Prompt | Workflow | RAG | Agent |
|----------|---------|----------|------|--------|
| Uses LLM | Yes | Sometimes | Yes | Yes |
| Multiple Steps | No | Yes | Yes | Yes |
| Planning | No | Fixed | Fixed | Dynamic |
| Decision Making | No | No | No | Yes |
| Uses External Data | No | Sometimes | Yes | Yes |
| Uses Vector Database | No | No | Yes | Optional |
| Uses APIs | No | Yes | Sometimes | Yes |
| Uses Memory | Limited | No | Optional | Yes |
| Autonomous | No | No | No | Yes |
| Can Take Actions | No | Sometimes | No | Yes |

---

# Real-World Example

Suppose you ask

```
Plan my vacation to Japan.
```

---

## Prompt

```
Suggest places to visit in Japan.
```

The LLM gives suggestions.

Done.

---

## Workflow

```
Get Budget

↓

Find Flights

↓

Find Hotels

↓

Generate Itinerary

↓

Send Email
```

Same sequence every time.

---

## RAG

```
Search Travel Documents

↓

Retrieve Visa Rules

↓

Retrieve Weather Information

↓

Generate Response
```

---

## Agent

```
Understand Goal

↓

Check Budget

↓

Search Flights

↓

Compare Hotels

↓

Retrieve Visa Rules

↓

Calculate Expenses

↓

Adjust Plan

↓

Book Tickets

↓

Create Calendar

↓

Email Itinerary
```

The sequence changes based on the situation.

---

# Final Hierarchy

```
                   AI Application

                         │

        ┌────────────────┴─────────────────┐

        │                                  │

   Traditional Workflow                AI Agent

        │                                  │

        │                          Uses Workflows

        │                          Uses RAG

        │                          Uses APIs

        │                          Uses Memory

        │                          Uses Planning

        │                          Uses Reasoning

        │

        └──────────────┐

                       ▼

              Large Language Model

                       ▲

                       │

                    Prompt
```

---

# Quick Summary

| Concept | Simple Meaning |
|----------|----------------|
| Prompt | A single instruction given to an AI model |
| Workflow | A predefined sequence of steps |
| RAG | Retrieve relevant information first, then generate an answer |
| AI Agent | An autonomous system that plans, reasons, uses tools, and performs actions to achieve a goal |

---

# Easy Way to Remember

- **Prompt = Ask**
- **Workflow = Follow Steps**
- **RAG = Search → Then Answer**
- **Agent = Think → Decide → Act → Repeat Until Goal is Achieved**

---

# Interview Questions

### Q1. What is a prompt?

A prompt is the instruction or input provided to a Large Language Model to generate a response.

---

### Q2. What is a workflow?

A workflow is a predefined sequence of tasks executed to complete a process.

---

### Q3. What is RAG?

Retrieval-Augmented Generation is an AI architecture that retrieves relevant information from an external knowledge source before generating a response.

---

### Q4. Why is RAG needed?

To reduce hallucinations, provide up-to-date information, and answer questions using private or organization-specific data.

---

### Q5. What is an AI agent?

An AI agent is a software system that uses an LLM, planning, memory, tools, and decision-making to autonomously accomplish user goals.

---

### Q6. Can an AI agent use RAG?

Yes. RAG is one of the tools or workflows an AI agent can invoke when it needs external knowledge to answer a question accurately.

---

## Conclusion

As AI systems evolve, they move from simple prompt-response interactions to sophisticated autonomous agents.

A useful mental model is:

```
Prompt  →  Workflow  →  RAG  →  AI Agent
```

Each stage builds on the previous one by adding more capability:

- **Prompt** provides a single instruction.
- **Workflow** organizes multiple fixed steps.
- **RAG** enriches responses with retrieved knowledge.
- **AI Agent** combines reasoning, planning, memory, tools, and workflows to achieve complex goals autonomously.
````
