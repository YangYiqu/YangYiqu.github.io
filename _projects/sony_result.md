---
title: "Sony Internship-LLM/AI"
excerpt: "- I have participated in and been responsible for implementing the feeding task instructions for a robot based on the Large Language Models (LLMs).

- My responsibility included completing Prompt Engineering, which involved designing the ReAct framework. This framework enables LLMs to interact with external tools to obtain additional information and generate inference paths and task-specific operations in an interleaved manner. By decomposing language instructions, I aimed to provide more reliable and practical responses.

- To achieve this, I utilized Grounded-Segment-Anything to implement the localization of specific objects in two-dimensional images and performed three-dimensional reconstruction of the coordinates. I further encapsulated these functions into an skill library.
  
- Our designed system can learn new skills from LLM's historical derivations and feedback, automatically adding these new skills to its skill vector library. During task completion, it will automatically select the required skills from the vector database based on relevance. It also incorporates a self-verification and self-correction module, which detects grammar and logic errors, providing feedback to LLM to revise solutions accordingly. Additionally, it utilizes environmental feedback to determine the successful implementation of tasks. "

collection: projects
---

- [Download sony_summary_final_version.pptx here](http://yangyiqu.github.io/files/sony_summary_final_version.pptx)

- [Click here to view Github (Partial) Code](https://github.com/YangYiqu/LLM_robot/tree/main) 
  
- Video Demo
 <!-- <br/><video id="video" controls="" preload="none" poster="封面"> -->
<video controls preload="none" style="width: 80%; height: auto;" poster="封面">
      <source id="mp4" src="/files/sony_demo.mp4" type="video/mp4"> </video>

---

# ReAct Framework - Technologies and Components

## 1. RAG (Retrieval-Augmented Generation)
📌 **Purpose**:

- Retrieve relevant skills from the **LangChain Chatchat vector skill library**.
- Combine the retrieved skills with the LLM to generate the final task planning and execution strategies.
- Improve the accuracy of information during robot interactions.

📌 **Details**:

- The framework uses **vector databases** to store skills and assist the LLM in generating optimal strategies by querying the most relevant skills.
- In complex task handling, the LLM optimizes itself by combining historical interaction data, aligning with RAG's idea of "combining retrieval with generation".

---

## 2. ReAct (Reasoning + Acting)
📌 **Purpose**:

- Allow the LLM not only to answer questions but also to perform reasoning, planning, and execution.
- The robot can **think about its current state**, query external information, and then act accordingly.

📌 **Details**:

- "ReAct" refers both to the framework's name and an interaction mode for the LLM.
- The LLM first performs **Reasoning**, then **Acts**.
- **Example**:
  - The robot reasons about the target position (combining **3D vision** data).
  - Queries the **LangChain vector skill library** to find the appropriate grabbing method.
  - Executes the grabbing task.

📌 **ReAct Paper (Google DeepMind)**:

- ReAct combines **Chain-of-Thought (CoT)** reasoning and **Action-based execution**, making it suitable for task planning and autonomous decision-making.

---

## 3. 3D Vision + Grounded Segmentation
📌 **Purpose**:

- The robot uses a **depth camera** and **3D reconstruction** to help the LLM understand environmental information.
- It combines **Grounding DINO** / **SAM (Segment Anything Model)** for semantic segmentation.

📌 **Details**:

- The robot retrieves information about the target object's position and then lets the LLM plan the path.
- **Example**:
  - The robot may ask, "Where is the red object on the table?"
  - The vision module segments the object and provides the data to the LLM.
  - The LLM combines the 3D coordinates with task planning and provides operation instructions.

---

## 4. LangChain + Vector Database
📌 **Purpose**:

- **LangChain** serves as the **Prompt Management** and **Memory Storage** component for the LLM.
- A **vector database** (FAISS / ChromaDB / Milvus) stores robot skills and user interaction history.

📌 **Details**:

- LangChain enables the LLM to remember tasks previously performed by the robot, avoiding redundant calculations.
- The robot automatically manages the skill library, supporting:
  - **Task Screening** 
  - **Skill Summarization**
  - **Self-verification**

---

## 5. Task Decomposition
📌 **Purpose**:

- The robot can break down complex tasks into smaller subtasks for gradual completion.
- **Example**:
  - 1. Retrieve object coordinates 🡪 2. Calculate grabbing angle 🡪 3. Perform grabbing 🡪 4. Place the object.

📌 **Details**:

- The LLM, combined with LangChain, manages tasks to ensure logical execution.
- When faced with new tasks, the robot can retrieve similar tasks from the skill library and generate an appropriate strategy.

---

## 6. Self-Learning & Feedback Loop
📌 **Purpose**:

- After task execution, the robot automatically summarizes its experience to improve future decision-making.
- With **LangChain Memory**, the robot can remember past mistakes and optimize strategies.

📌 **Details**:

- **Task feedback** (success or failure) 🡪 **Update skill library** 🡪 **Optimize LLM prompts**.
- Over time, the robot becomes smarter in the same scenario through long-term interaction memory.

---

## Summary: Technologies in ReAct Framework

| **Technology**                     | **Role in ReAct Framework**                                                       |
|-------------------------------------|-----------------------------------------------------------------------------------|
| **RAG (Retrieval-Augmented Generation)** | Retrieves relevant skills from the vector skill library to improve task execution accuracy. |
| **ReAct (Reasoning + Acting)**      | Enables the robot to reason and execute tasks, facilitating autonomous decision-making. |
| **3D Vision + Grounded Segmentation** | Helps the LLM understand the robot's environment and plan tasks accordingly.        |
| **LangChain + Vector Database**     | Stores task information, historical interactions, and manages skills.              |
| **Task Decomposition**              | Breaks complex tasks into smaller steps to improve execution efficiency.            |
| **Self-Learning (Feedback Loop)**   | Optimizes robot skills based on task performance and feedback, enhancing future task success. |
