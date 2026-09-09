#  AI-Powered Mystery Case Analysis and Investigation Assistant

##  🔗 Live Application
AI Mystery Solver :
https://udify.app/workflow/2YW6WvJnDFBUwPV5


---

##  Project Overview

AI Mystery Solver is an AI-powered investigation assistant designed to help users analyze new mystery cases and investigation-related situations.

The user does not need to upload a PDF or any case document. Instead, the user can directly enter the details of a mystery case and ask questions.

The system uses **RAG (Retrieval-Augmented Generation)** to retrieve relevant general investigation knowledge from a Knowledge Base. The retrieved information is then provided to **GPT-OSS 120B**, which analyzes the user's case and generates useful investigation guidance.

The system can help identify possible suspects, important clues, possible evidence, timelines, motives, connections, theories, and recommended next investigation steps.

---

##  Objectives

- Analyze new mystery cases using AI.
- Allow users to directly enter case details.
- Avoid requiring users to upload a case PDF.
- Retrieve relevant investigation knowledge using RAG.
- Identify possible suspects and clues.
- Analyze evidence and timelines.
- Suggest possible motives and theories.
- Recommend useful next investigation steps.
- Provide clear and simple investigation guidance.
- Avoid declaring a person guilty without sufficient evidence.

---

##  Problem Statement

Traditional mystery analysis systems may depend on a fixed case document or PDF. The user has to upload a document and ask questions only about that particular case.

This approach is not flexible for new mystery situations.

There is a need for a general AI investigation assistant where users can directly describe a new mystery case and receive investigation guidance based on general investigation knowledge.

---

##  Proposed Solution

The proposed system is a **General AI Mystery Investigation Assistant**.

Users can directly type a new mystery situation, including available facts, suspects, clues, evidence, locations, and timings.

The system retrieves relevant investigation knowledge from the Knowledge Base using RAG. GPT-OSS 120B then analyzes the user's case along with the retrieved knowledge and provides investigation guidance.

The system can suggest possible suspects, clues, evidence to verify, timelines, motives, connections, theories, and next investigation steps.

---

##  How RAG Is Used

RAG stands for **Retrieval-Augmented Generation**.

RAG combines:

1. Knowledge Retrieval
2. Relevant Knowledge
3. Large Language Model
4. Generated Answer

The Knowledge Base contains **general investigation knowledge**, not a fixed mystery case.

When the user enters a new case, the Knowledge Retrieval node searches for relevant investigation information.

The retrieved knowledge is given to GPT-OSS 120B.

GPT-OSS 120B uses both the user's case details and the retrieved knowledge to generate the final answer.

---

##  Knowledge Base

### Knowledge Base Name

**Mystery Investigation Knowledge**

The Knowledge Base contains general investigation information such as:

- Evidence Analysis
- Suspect Analysis
- CCTV Investigation
- Fingerprint Evidence
- Alibi Verification
- Witness Statement Analysis
- Clue Analysis
- Timeline Analysis
- Motive Analysis
- Investigation Methods

The Knowledge Base does not contain a specific user's mystery case.

---

##  General Investigation Knowledge

### 1. Evidence Analysis

Physical and digital evidence can help investigators understand a case.

Examples include fingerprints, CCTV footage, access records, photographs, objects, timestamps, and witness statements.

Evidence should be compared and verified before reaching a conclusion.

---

### 2. Suspect Analysis

A suspect can be analyzed based on:

- Access
- Opportunity
- Motive
- Location
- Behavior
- Statements
- Relationship with the victim
- Evidence connected to the suspect

Being a suspect does not mean the person is guilty.

---

### 3. CCTV Investigation

CCTV footage can help identify:

- Movement of people
- Locations
- Entry and exit times
- Activities
- Interactions

Missing, interrupted, or unavailable CCTV footage may also require further investigation.

---

### 4. Fingerprint Evidence

Fingerprints may help connect a person to an object or location.

Investigators should verify where and when the fingerprint was found before drawing conclusions.

---

### 5. Alibi Verification

An alibi is a claim that a person was somewhere else when an incident happened.

An alibi can be checked using:

- CCTV
- Witnesses
- Access records
- Digital timestamps
- Phone or location records where legally available
- Other reliable evidence

---

### 6. Witness Statement Analysis

Witness statements should be compared with other evidence.

Investigators can check:

- Differences between statements
- Time inconsistencies
- Location inconsistencies
- Missing information
- Contradictions with physical evidence

---

### 7. Clue Analysis

Clues should be connected with:

- Suspects
- Evidence
- Timeline
- Locations
- Witness statements

A single clue should not automatically be treated as proof.

---

### 8. Timeline Analysis

Timeline analysis helps understand what happened:

- Before the incident
- During the incident
- After the incident

Important timestamps should be compared to identify inconsistencies and possible connections.

---

### 9. Motive Analysis

Possible motives may include:

- Financial gain
- Personal conflict
- Revenge
- Jealousy
- Opportunity
- Relationship problems

Motive alone does not prove that a person committed a crime.

---

### 10. Investigation Methods

A general investigation can include:

- Collecting available evidence
- Verifying statements
- Checking CCTV
- Comparing timelines
- Checking access records
- Identifying connections
- Analyzing clues
- Considering multiple theories
- Identifying missing information
- Recommending further investigation steps

---

##  System Workflow

The main Dify workflow is:

    User Input
         ↓
    Knowledge Retrieval
         ↓
    GPT-OSS 120B
         ↓
    Answer

### Detailed Flow

    New User Case + Question
              ↓
       Knowledge Retrieval
              ↓
    General Investigation Knowledge
              ↓
     Relevant Knowledge Retrieved
              ↓
        GPT-OSS 120B
              ↓
         Case Analysis
              ↓
            Answer

---

##  Technologies Used

- Dify
- Generative AI
- GPT-OSS 120B
- RAG
- Knowledge Base
- Knowledge Retrieval
- LLM
- Prompt Engineering

---

##  Dify Implementation

### Step 1: Create Knowledge Base

Open Dify.

Go to:

**Knowledge → Create Knowledge**

Create a Knowledge Base named:

**Mystery Investigation Knowledge**

Add general investigation knowledge instead of uploading a fixed mystery case PDF.

---

### Step 2: Add Investigation Knowledge

Add information related to:

- Evidence
- Suspects
- CCTV
- Fingerprints
- Alibis
- Witnesses
- Clues
- Timelines
- Motives
- Investigation methods

Process and save the Knowledge Base.

---

### Step 3: Create Chatflow

Create a new Chatflow in Dify.

Add the following nodes:

**User Input → Knowledge Retrieval → LLM → Answer**

---

### Step 4: Configure User Input

The user enters a new mystery case directly.

Example:

My diamond disappeared from a locked room at 10 AM. Ravi was near the room at that time. Priya had access to the room. The CCTV stopped at 9:50 AM. Who should I investigate first?

---

### Step 5: Configure Knowledge Retrieval

Add the **Knowledge Retrieval** node.

Select:

**Mystery Investigation Knowledge**

Use the user's question/case as the Query Text.

Depending on the Dify interface, the input variable may appear as:

**sys.query**

or:

**User Input → queryString**

Use the variable provided by the User Input node.

---

### Step 6: Retrieval Settings

Recommended initial settings:

- Retrieval Method: Vector Search
- Top K: 3 or 5
- Score Threshold: Default initially

The system retrieves the most relevant investigation knowledge for the user's case.

---

##  GPT-OSS 120B Prompt

Use the following prompt in the LLM node:

You are an AI Mystery Investigation Assistant.

Analyze the user's case carefully and provide useful investigation guidance.

Use the relevant information retrieved from the Knowledge Base.

Identify:

1. Possible suspects
2. Important clues
3. Possible evidence
4. Timeline
5. Possible motives
6. Connections between clues and suspects
7. Possible theories
8. Recommended next investigation steps

Do not accuse anyone as definitely guilty.

Clearly separate facts from assumptions.

If there is not enough information, say that more information is needed.

Consider multiple possibilities instead of making an immediate conclusion.

Give the answer in simple and clear language.

---

##  Example User Input

My diamond disappeared from a locked room at 10 AM. Ravi was near the room at that time. Priya had access to the room. The CCTV stopped at 9:50 AM. Who should I investigate first?

---

## 🔎 Example Analysis

### Possible Suspects

Ravi and Priya may require further investigation because Ravi was near the room and Priya had access.

### Important Clues

- Ravi was near the room.
- Priya had room access.
- CCTV stopped at 9:50 AM.
- Diamond disappeared at 10 AM.

### Evidence to Check

- CCTV before it stopped.
- Access records.
- Fingerprints.
- Witness statements.
- Door or lock condition.
- Timeline of each person's movements.

### Timeline

- 9:50 AM — CCTV stopped.
- 10:00 AM — Diamond was discovered missing.

The CCTV interruption is an important point that requires verification.

### Possible Motives

A possible motive cannot be determined from the available information.

More information about relationships, access, and circumstances is needed.

### Recommended Next Steps

1. Investigate why the CCTV stopped.
2. Verify who had access to the room.
3. Check Ravi's movements.
4. Verify Priya's access and movements.
5. Examine the lock and room.
6. Check fingerprints and other evidence.
7. Compare witness statements.
8. Build a complete timeline.

The AI should not declare Ravi or Priya guilty without sufficient evidence.

---

##  Key Features

###  Mystery Case Analysis

Analyzes new mystery cases entered directly by the user.

###  Suspect Identification

Identifies people who may require further investigation based on available facts.

###  Clue Analysis

Connects clues with suspects, evidence, locations, and timelines.

###  Timeline Analysis

Organizes important events and timestamps.

###  CCTV Analysis Guidance

Suggests what CCTV information should be checked.

###  Evidence Analysis

Identifies evidence that may help verify the case.

###  Motive Analysis

Suggests possible motives when sufficient information is available.

###  Connection Analysis

Finds possible relationships between suspects, clues, evidence, and events.

###  Investigation Guidance

Provides recommended next steps for investigation.

###  Multiple Theories

Considers more than one possible explanation.

### Responsible AI

The system does not automatically declare anyone guilty.

---

##  Traditional System vs Proposed System

| Traditional System | Proposed AI Mystery Solver |
|---|---|
| Depends on a fixed case document | Works with new cases |
| User may need to upload PDF | No case PDF upload required |
| Limited to stored case information | Uses general investigation knowledge |
| Answers questions about one case | Analyzes different mystery situations |
| Less flexible | More flexible |
| Static case analysis | Dynamic case analysis |

---

##  RAG vs Fixed PDF

A fixed PDF-based system stores information about one specific mystery case.

The proposed system instead stores **general investigation knowledge** in the Knowledge Base.

The user's new case is entered directly during runtime.

RAG retrieves the investigation knowledge relevant to the user's situation.

Therefore, the system can be used for different mystery cases without requiring the user to upload a new case PDF every time.

---

##  Sample Questions

Users can ask questions such as:

- Who should I investigate first?
- What clues are important in this case?
- What evidence should I check?
- What should I verify about the suspects?
- Can you create a timeline?
- What possible motives should be considered?
- Are there contradictions in the statements?
- What CCTV information should be checked?
- What evidence can confirm or reject this theory?
- What should I investigate next?
- What information is missing from this case?
- What are the possible theories?
- How are the suspects connected?
- Which clues need further verification?

---

##  Testing

The system can be tested using different mystery scenarios.

### Test Case 1

A valuable object disappears from a locked room.

The user provides:

- Time of disappearance
- People with access
- CCTV information
- Location
- Available clues

The AI should identify possible suspects and recommend evidence to check.

### Test Case 2

A person claims they were somewhere else during an incident.

The AI should recommend alibi verification using available evidence.

### Test Case 3

Two witnesses provide different statements.

The AI should identify the inconsistency and recommend comparing the statements with other evidence.

### Test Case 4

CCTV footage stops before an incident.

The AI should identify the CCTV interruption as an important point for investigation.

---

##  Why GPT-OSS 120B?

GPT-OSS 120B is used as the main LLM to analyze the user's case and generate the final investigation response.

It receives:

- User's case details
- User's question
- Retrieved investigation knowledge

It then generates a structured investigation response.

---

##  Why Knowledge Retrieval?

Knowledge Retrieval helps the LLM access relevant investigation knowledge instead of depending only on its general knowledge.

For example:

If the user asks about an alibi, the system can retrieve information about **Alibi Verification**.

If the user asks about fingerprints, it can retrieve information about **Fingerprint Evidence**.

If the user asks about CCTV, it can retrieve information about **CCTV Investigation**.

This makes the response more relevant to the user's investigation question.

---

##  Why RAG?

RAG improves the system by combining retrieval and generation.

The system first retrieves relevant knowledge.

Then the LLM uses that knowledge to generate an answer.

Therefore:

**Retrieval + Generation = RAG**

---

##  Responsible AI

The system is designed to provide investigation guidance rather than make final legal judgments.

Important principles:

- Do not automatically declare someone guilty.
- Treat suspects as possible persons of interest.
- Separate facts from assumptions.
- Consider multiple possibilities.
- Recommend verification of evidence.
- Identify missing information.
- Encourage evidence-based conclusions.

---

##  Limitations

- The system cannot replace professional investigators.
- AI-generated suggestions may not always be correct.
- The quality of analysis depends on the information provided by the user.
- Missing information can affect the result.
- AI should not be treated as a legal authority.
- Real investigations require proper evidence collection and professional procedures.

---

##  Future Enhancements

Future versions can include:

- Voice-based case input
- Image-based clue analysis
- CCTV video analysis
- Automatic timeline generation
- Graph-based suspect relationship analysis
- Evidence ranking
- Case history management
- Interactive investigation dashboard
- Multi-language support
- Advanced forensic knowledge
- Automated case report generation

---

##  Project Structure

    AI-Mystery-Solver/
    │
    ├── README.md
    │
    ├── Knowledge-Base/
    │   └── Mystery-Investigation-Knowledge
    │
    ├── Dify-Workflow/
    │   └── Chatflow
    │
    ├── Screenshots/
    │   ├── workflow.png
    │   ├── knowledge-base.png
    │   ├── retrieval.png
    │   └── final-output.png
    │
    └── Documentation/
        └── Project-Documentation

---


##  Learning Outcomes

Through this project, we learn:

- Generative AI
- Large Language Models
- GPT-OSS
- RAG
- Knowledge Retrieval
- Knowledge Base creation
- Prompt Engineering
- Dify workflow creation
- AI-based reasoning
- Responsible AI
- Investigation-oriented AI applications

---

##  Advantages

- No need to upload a mystery PDF.
- Can handle different new mystery cases.
- Easy for users to enter case details.
- Uses RAG for relevant investigation knowledge.
- Provides structured analysis.
- Helps organize clues and timelines.
- Suggests evidence to verify.
- Provides possible theories.
- Recommends next investigation steps.
- More flexible than a fixed-case chatbot.

---

##  Use Cases

The AI Mystery Solver can be used for:

- Mystery case analysis
- Educational investigation activities
- Crime investigation learning
- Detective-style problem solving
- Case study analysis
- Forensic learning
- Investigation training
- Logical reasoning exercises

---

##  Project Information

**Project Name:** AI-Powered Mystery Case Analysis and Investigation Assistant

**Short Name:** AI Mystery Solver

**Platform:** Dify

**AI Model:** GPT-OSS 120B

**Architecture:** RAG

**Knowledge Source:** General Investigation Knowledge

**Main Technique:** Retrieval-Augmented Generation

---


##  Conclusion

AI Mystery Solver is a flexible AI-powered investigation assistant that helps users analyze new mystery cases without requiring them to upload a specific case PDF.

The system uses RAG to retrieve relevant general investigation knowledge and GPT-OSS 120B to analyze the user's case.

It can identify possible suspects, clues, evidence, timelines, motives, connections, theories, and recommended next steps.

The main goal is to provide useful, structured, and responsible investigation guidance while keeping the final conclusion evidence-based.

---

##  Final Summary

**User enters a new mystery case → RAG retrieves relevant investigation knowledge → GPT-OSS 120B analyzes the case → AI provides investigation guidance.**

The proposed system is therefore a **General AI Mystery Investigation Assistant**, rather than a chatbot limited to one uploaded mystery PDF.
