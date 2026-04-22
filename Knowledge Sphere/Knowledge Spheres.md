# Knowledge Spheres

*Source: Notion — https://www.notion.so/3026abe00ba480eea38cd4d300fef27a (Initiative Tracker)*

## Inputs
- Voice to text transcript
- Documents
- Video transcripts

## Schema
**Multi-dimension.** It is **not** a filing cabinet or folder. It is a set of tags we attach to every chunk.

Supposedly: Who, what, what-definition.

**Shift thinking from "Where do I file this?" to "What are its attributes?"**

- **Dimension 1: Swim Lane (Context)** — Who is this for? (Sales, Marketing, Operations, Art, Production, etc.)
- **Dimension 2: Subject (Noun)** — What specific thing are we talking about? (Latex Printer, Invoice, Vehicle Wrap, Forklift, Employees)
- **Dimension 3: Intent (Verb)** — What kind of knowledge is this? (SOP, Troubleshooting) — *this dimension is difficult to answer; "verb" or "intent" may need changing*

### Example JSON
```json
{
  "source_text": "Hey, when you're doing the final heat post...",
  "refined_content": "Ensure post-heating of deep channels on Sprinter vans reaches 180 degrees to prevent vinyl lifting.",
  "metadata": {
    "swim_lane": "Production",
    "subject": "Vehicle Wrap",
    "intent": "Troubleshooting",
    "tags": ["Sprinter Van", "Temperature", "Vinyl Failure"]
  }
}
```

## The Ingestion Pipeline

```mermaid
flowchart TD
    classDef smart fill:#f96,stroke:#333,stroke-width:2px,color:black;
    classDef dumb fill:#9cf,stroke:#333,stroke-width:1px,color:black;
    classDef store fill:#ddd,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5,color:black;

    subgraph Input ["Step 1: Input & Raw Processing (Low Power)"]
        A[Voice Note / PDF] -->|Input| B[Transcription Node]
        B -->|Output: Raw Text| C[Chunking Node]
        C -->|Action: Split with Overlap| D(Text Chunk)
    end

    subgraph Intelligence ["Step 2: The 'Micro-Agent' (Requires High IQ)"]
        D -- "Input Text" --> E{Enrichment Agent}
        E -- "Analyzes Context" --> F[Extract 'Knowledge Sphere' Tags]
        F -->|Dimension 1| G["Swim Lane: Who?"]
        F -->|Dimension 2| H["Subject: What?"]
        F -->|Dimension 3| I["Intent: Why?"]
        G & H & I --> J[Metadata JSON Object]
    end

    subgraph Math ["Step 3: The Embedding (Requires Low Power)"]
        D -- "Same Input Text" --> K["Embedding Model (The 'Map Maker')"]
        K -- "Converts to Numbers" --> L["Vector"]
    end

    subgraph Storage ["Step 4: The Vector Database"]
        J --> M[(Vector DB Record)]
        L --> M
        D -->|Original Text| M
    end

    class B,C,D,K,L dumb;
    class E,F,G,H,I,J smart;
    class M store;
```

### Why this distinction matters for hardware
- **Blue Nodes (Low Power):** Whisper (Transcription) and Embedding Model run on a current Intel Ultra laptop. Efficient.
- **Orange Nodes (High IQ):** **Only** place you need the $4,000 Mac Studio or Dual RTX 4090s. The "Enrichment Agent" must intelligently tag messy sentences.

### The Retrieval Flow (Hybrid Search)

```mermaid
flowchart LR
    User[User Query] -->|"How do I fix the van heater?"| Search[Search System]
    subgraph "Hybrid Search"
        Search -->|1. Vector Search| A[Find content mathematically close]
        Search -->|2. Metadata Filter| B[Filter: Subject + Intent]
    end
    A & B --> Result[Perfect Result]
```

## Recommended Hardware

**System:** Lenovo ThinkCentre M90s Gen 6 (Intel) Small Form Factor (SFF)
- **CPU:** Intel® Core™ Ultra 5 225
- **OS:** Windows 11 Pro 64 (or Ubuntu 24.04 LTS)
- **Memory:** 32 GB DDR5-5600MHz (2×16 GB dual-channel)
- **GPU:** NVIDIA® GeForce RTX™ 3050 6GB GDDR6
- **Storage:** 1 TB SSD M.2 2280 PCIe Gen4
- **PSU:** 310W or 380W (required to support GPU)
- **Networking:** Intel® I219-LM + Wi-Fi 6E AX211

### Ubuntu Compatibility
- **Yes, it works.** Lenovo officially certified M90s Gen 6 for Ubuntu 24.04 LTS.
- **MUST install Ubuntu 24.04 LTS (Noble Numbat) or newer.** 22.04 uses kernel 5.15 which doesn't know E-cores or NPU.
- Ubuntu 24.04 ships with Kernel 6.8+ including initial support for your Intel Ultra chip.

## Local + Cloud Hybrid Architecture

```mermaid
flowchart TD
    subgraph User_Office ["Local (ThinkCentre M90s)"]
        Start((Incoming File)) -->|Voice Note| A[Whisper Transcription]
        A -->|Raw Text| B[Code Node: Chunking]
        B -->|1. Context Only| C{API Gateway}
        B -->|2. Chunk Text| D[Ollama: Embeddings]
        C -.->|Returns JSON Tags| E[Merge Data]
        D -->|Returns Vector| E
        E -->|Text + Tags + Vector| F[(Local Vector DB)]
    end
    subgraph Internet ["Cloud Layer"]
        C -->|Secure TLS| CloudAI[Claude Haiku/Sonnet]
        CloudAI -->|Analyze & Tag| C
    end
```

**Architecture principle:** Only the chunk context (not the content) goes to cloud AI for tagging. Embeddings and storage stay local.
