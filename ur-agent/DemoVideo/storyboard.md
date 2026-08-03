# UR-Agent Demo Video Storyboard and Voice-Over Script

## 1. Video goal

- Keep the video between 3 and 5 minutes.
- Show that UR-Agent is a Track 2 private AI Agent deployed locally with AMD Radeon GPU + ROCm.
- Demonstrate at least 3 of the following capabilities: RAG, tool calling, multi-step planning, multi-turn memory, and permission isolation. The recommended target is to show all 5.
- Keep command-line output or runtime logs visible enough to prove that core inference uses the local llama.cpp ROCm service.

## 2. Pre-recording checklist

- [ ] Hide or mask all API keys, SSH private keys, database passwords, and real private data.
- [ ] Increase terminal font size so it is readable in the recording.
- [ ] Prepare `rocm-smi`, the llama.cpp server, the FastAPI backend, and the Vue or Gradio UI.
- [ ] Prepare two demo spaces, such as a personal space and a Seller space.
- [ ] Prepare a short project description that can be inserted into the knowledge base.
- [ ] Prepare performance data: GPU model, model name, quantization level, VRAM usage, and tokens/s.

## 3. Storyboard

| Time | Screen | Action | Voice-over point |
| :--- | :--- | :--- | :--- |
| 00:00-00:20 | Title page or project README | Show application name, track, and applicant | UR-Agent is a local private resource management Agent |
| 00:20-00:50 | Terminal | Run `rocm-smi` and show AMD Radeon GPU status | Core inference runs on AMD Radeon GPU + ROCm |
| 00:50-01:20 | Terminal | Show llama.cpp ROCm server logs | The local model exposes an OpenAI-compatible API |
| 01:20-01:45 | Backend and frontend | Start FastAPI and the Vue/Gradio interface | Agent service, tool layer, and UI all run locally |
| 01:45-02:20 | Chat UI | Insert project knowledge and ask a related question | Demonstrate local RAG |
| 02:20-03:00 | Chat UI | Enter a compound task, such as "find resources, identify risks, and create an action plan" | Demonstrate tool calling and multi-step planning |
| 03:00-03:30 | Chat UI | Follow up with "keep only the three most urgent items" | Demonstrate multi-turn memory |
| 03:30-04:10 | Space switch | Switch to another organization space and query similar data | Demonstrate `puid` + `ouid` permission isolation |
| 04:10-04:40 | Terminal or PPT page | Show performance metrics and GPU usage | Explain quantization, GPU offload, and context trimming |
| 04:40-05:00 | Summary page | Show source link, demo website, and MIT license | Emphasize private local deployment, customization, and reproducibility |

## 4. Recommended demo prompts

RAG demo:

```text
Store this project description in the current space knowledge base, then summarize the core value of UR-Agent in three sentences.
```

Tool calling demo:

```text
Check the resources, finance records, and knowledge entries in the current space. Identify the three highest-priority risks and produce an action checklist.
```

Multi-turn memory demo:

```text
Compress the action checklist above into three tasks that can be completed this afternoon.
```

Space isolation demo:

```text
After switching to the Seller space, check inventory and orders, and explain why it cannot see the personal-space materials from the previous step.
```

## 5. Full voice-over script

Hello, I am qiancy, AMD Developer Program number 00000657. This project is UR-Agent, short for Uni-Resource Agent. It is submitted to the 2026 AMD AI DevMaster Hackathon Track 2: Development and Local Deployment of Private AI Agents.

The core idea of UR-Agent is Everything is a Resource. It represents assets, knowledge, people, financial transactions, products, and tasks from personal, family, small organization, and business scenarios as resources. The Agent can retrieve, analyze, and operate on those resources in a local environment.

First, let's look at the runtime environment. This deployment uses AMD Radeon GPU and ROCm. The core language model runs through a llama.cpp ROCm backend and exposes a local OpenAI-compatible API. The FastAPI backend, database, vector retrieval, and frontend interface all run locally. Core data is not processed by a remote closed Agent platform.

Now I will demonstrate the local knowledge base. I insert a piece of project information into the current space and then ask the Agent about its core value. The Agent first retrieves relevant content from the knowledge collection of the current organization space, then uses the local model to generate the answer. This shows private local RAG.

Next, I will demonstrate tool calling and multi-step planning. I enter a compound task that asks the Agent to inspect resources, finance records, and knowledge entries, identify risks, and create an action checklist. The Agent selects tools based on the task, reads structured data, combines knowledge retrieval results, and then produces actionable recommendations.

Then I continue with a follow-up request and ask it to compress the previous checklist into three tasks that can be completed this afternoon. This demonstrates local multi-turn memory. The Agent understands the previous turn instead of treating each question as an isolated request.

Finally, I switch to another space, such as the Seller space. UR-Agent uses `puid` and `ouid` in JWT to bind the person and organization context. Every tool call is filtered by the current space, so data does not leak across personal, family, business, and Seller contexts. This is an important privacy and permission boundary for a private Agent.

For performance, the project uses GGUF quantized models, ROCm GPU offload, context trimming, vector indexes, and controlled tool result fields to reduce VRAM usage and improve response speed. The final submission materials record the measured GPU model, ROCm version, tokens per second, and end-to-end latency.

The production demo website is https://rc-f3d13324264295f3.radeon.firstdg.ai. The source code is licensed under MIT and will be submitted at https://github.com/qiancy/ur-agent. Thank you.
