### 🧭 How to read this diagram

The diagram represents a **real production-grade workflow** implemented in n8n and should be read **from left to right**.

**Key reading principles:**

- **Each block** corresponds to a logical processing stage or a group of workflow nodes.
- **Arrows** indicate data and control flow.
- The workflow follows the principle: **one item = one full processing cycle**.

**Main stages:**

1. **Notion Database → Workflow Trigger**  
   The workflow starts for records with status `Ready to process`.

2. **Loop / Condition Check**  
   Each record is processed individually within a loop.

3. **Unified Input Builder**  
   All incoming data (text, screenshots, images) is aggregated and normalized into a single input object.

4. **Entry Assistant (AI Agent #1)**  
   The agent extracts and structures factual data into a strictly validated JSON format.

5. **Location Assistant (AI Agent #2)**  
   The second agent generates a neutral, SEO-friendly description using the first agent’s output and the original context.

6. **Merge & Validation Layer**  
   Data is filtered according to the rule:  
   *only empty and explicitly allowed fields can be updated*.

7. **Notion Update Payload**  
   A safe update payload is built with no risk of overwriting existing data.

8. **Update & Status Management**  
   - on success: status → `Ready to check`  
   - on error: status → `Error` with error logging

9. **Loop Back**  
   After processing one record, the workflow returns to the beginning to handle the next item.

The diagram highlights a **controlled LLM integration**, where AI models are embedded into business logic rather than operating as uncontrolled data writers.
