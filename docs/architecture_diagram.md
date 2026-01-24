```mermaid
flowchart LR

A["Notion Database<br/>Automation Status = Ready to process"]
--> B["Workflow Trigger<br/>Get many database pages"]

B --> C["Loop Over Items<br/>Process one page"]

C --> D["Unified Input Builder & Normalize<br/>Text + Screenshots + Photos"]
D --> E["Entry Assistant<br/>AI Agent 1<br/>Data Extraction"]
E --> F["Parse & Normalize Output<br/>Safe JSON"]
F --> G["Location Assistant<br/>AI Agent 2<br/>Description Generation"]
G --> H["Merge & Validation Layer<br/>Only Empty Fields"]
H --> I["Build Notion Update Payload<br/>No Overwrite Logic"]
I --> J["Update Notion Page"]

J --> K1["Set Automation Status<br/>Ready to check"]
J -->|Error| K2["Set Automation Status<br/>Error + Log"]

K1 --> C
K2 --> C
