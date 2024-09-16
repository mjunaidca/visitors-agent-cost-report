# Visitors Chatbot

## Initial Cost Analysis

Here’s a clear and structured way to present the **individual message cost breakdown** and **cost per day for different user volumes**, including caching storage.

---

### **1. Individual Message Cost Breakdown (Without Storage)**

| **Cost Component**         | **Token Count (per message)**  | **Rate per Million Tokens**   | **Cost per Message**     |
|----------------------------|-------------------------------|-------------------------------|--------------------------|
| **Input Tokens**            | 640 tokens (40 query + 600 history) | $0.075 / million tokens       | \( \frac{640}{1,000,000} \times 0.075 = \) **$0.000048** |
| **Output Tokens**           | 140 tokens                    | $0.30 / million tokens         | \( \frac{140}{1,000,000} \times 0.30 = \) **$0.000042**   |
| **Context Caching (Usage)** | 34,000 tokens                 | $0.01875 / million tokens      | \( \frac{34,000}{1,000,000} \times 0.01875 = \) **$0.0006375** |
| **Total Cost per Message**  |                               |                               | **$0.00073**              |

---

### **2. Per Day and 30 Days Total Cost for Different User Volumes (Including Fixed Cache Storage Cost)**

#### Assumptions:
- **Each user sends 20 queries per day**.
- **Fixed Cache Storage Cost**: $0.84/day.
- **30 days** considered for monthly calculations.

#### **Per Day and 30-Day Cost (with 20 queries per user)**

| **Users per Day**   | **Total Messages per Day** | **Message Cost per Day**    | **Fixed Cache Storage Cost per Day** | **Total Daily Cost**     | **Total Cost for 30 Days**   |
|---------------------|----------------------------|-----------------------------|--------------------------------------|--------------------------|------------------------------|
| **200 users/day**    | \( 200 \times 20 = 4,000 \) messages | \( 4,000 \times 0.00073 = 2.92 \)    | **$0.84/day**                         | \( 2.92 + 0.84 = \) **$3.76/day**  | \( 3.76 \times 30 = \) **$112.80**  |
| **500 users/day**    | \( 500 \times 20 = 10,000 \) messages | \( 10,000 \times 0.00073 = 7.30 \)   | **$0.84/day**                         | \( 7.30 + 0.84 = \) **$8.14/day**  | \( 8.14 \times 30 = \) **$244.20**  |
| **1,000 users/day**  | \( 1,000 \times 20 = 20,000 \) messages | \( 20,000 \times 0.00073 = 14.60 \)  | **$0.84/day**                         | \( 14.60 + 0.84 = \) **$15.44/day** | \( 15.44 \times 30 = \) **$463.20** |
| **2,000 users/day**  | \( 2,000 \times 20 = 40,000 \) messages | \( 40,000 \times 0.00073 = 29.20 \)  | **$0.84/day**                         | \( 29.20 + 0.84 = \) **$30.04/day** | \( 30.04 \times 30 = \) **$901.20** |

---

### **Footnotes:**

1. **Context Caching Storage Cost**:
   - In addition to the per-message cost, there is a **fixed cost of $0.84/day** for storing 34,000 tokens as cached content.

2. **Compute Cost**:
   - The **compute cost** for running the FastAPI service on **Azure Container Apps Service** is **not included** in the above calculations. As previously estimated, this compute cost is approximately **$23.44/month**.

This breakdown offers a clear view of the costs involved in running the chatbot for different user volumes, including token usage and fixed caching storage costs.

