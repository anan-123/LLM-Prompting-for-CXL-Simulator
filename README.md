# LLM-Prompting-for-CXL-Simulator

**Extending architectural simulators for emerging memory technologies using Large Language Models (LLMs)**

---

## Project Overview

This research explores the feasibility of using Large Language Models (ChatGPT, Claude) to extend the VANS (Validated cycle-Accurate NVRAM Simulator) with support for CXL (Compute Express Link) memory simulation. Instead of manual coding, we apply advanced prompt engineering techniques to generate simulator code automatically.

**Goal:** Build a CXL-capable simulator by leveraging LLMs to extend existing architectural simulators without starting from scratch.

---

## Key Research Questions

- Can LLMs effectively extend complex architectural simulators?  
- Which prompting strategies best support systems-level code generation?  
- What are the capabilities and limitations of AI-assisted simulator development?  
- How does LLM-generated code compare with traditional development methods?

---

## Architecture

- **Base Simulator:** VANS — a cycle-accurate event-driven simulator for Optane DIMM microarchitecture  
- **Target Extension:** CXL memory device and system integration  
- **LLMs Used:** Claude 3.5 Sonnet and GPT-3.5/4 Turbo for automated code generation

### Core Components Generated

src/
├── cxl_memory.cpp/h - CXL Type 3 memory device model with protocol-level latency
├── cxl_system.cpp/h - Memory controller and request routing management
├── factory.cpp - Extended component factory for CXL registration
├── vans.cpp - Modified integration layer with CXL support
└── config/
└── cxl_config.cfg - CXL-specific configuration parameters

### System Integration

The CXL extension integrates with VANS through:  

- **Modular Architecture:** Maintains VANS component structure  
- **Factory Pattern:** Enables configurable CXL memory instantiation  
- **Event-Driven Model:** Preserves cycle-accurate simulation timing  
- **Memory Hierarchy:** Supports local DRAM + CXL memory configurations  

---

## Experimental Methodology

To design effective prompts for building CXL-VANS, ideas from [4], [5], and [6] were referenced. Various prompting techniques were experimented with, described below:

### 3.1 Zero Shot Prompting

- Uses a single prompt with all details.  
- Relies on LLM’s retrieval-augmented generation capabilities.  
- Lacks deeper context for complex tasks.

### 3.2 Role-based Prompting

- Assigns a specific role to the LLM (e.g., system architect).  
- Provides detailed file structure and architecture context.  
- Effective for complex coding and system-level reasoning.  

### 3.3 Few-shot Learning

- Supplies example code snippets as references.  
- Helps with pattern-based or repetitive code generation.  
- Performance depends on example quality, less adaptable to new methods.

### 3.4 Chain-of-Thought (CoT) Prompting

- Breaks complex tasks into step-by-step reasoning.  
- Produces organized solutions but may diverge from original structure.

### 3.5 Iterative Refinement Prompting

- Multiple rounds of interaction and code refinement.  
- Effective for debugging and improving code quality over iterations.

---

## Results Summary

### LLM Efficiency

- Average Token Consumption: ~1000 tokens per session  
- Generation Time: Seconds to minutes per iteration  
- Refinement Cycles: Typically 2-3 for production-ready code  
- Success Rate: Varies by prompting technique

---

## 🔍 Key Findings

### ✅ Strengths of LLM-Assisted Development

- Rapid Prototyping: Quick boilerplate code generation  
- Documentation: Clear explanation of complex concepts  
- Integration Planning: Clear architectural outlines  
- Debugging Assistance: Good at spotting common errors  
- Code Clarity: Produces clean, readable code

### ⚠️ Limitations Identified

- Complex Integration: Difficulty with system-level interconnections  
- Domain Expertise: Needs extensive context for specialized domains  
- File Structure Awareness: Requires explicit architectural guidance  
- Optimization: Limited performance tuning capabilities  
- Error Propagation: Errors can compound over iterations

### 🎯 Best Practices Discovered

- Provide Explicit File Structure: Crucial for integration success  
- Use Iterative Refinement: 2-3 cycles usually needed  
- Combine Techniques: Hybrid prompting most effective  
- Validate Early: Testing at each iteration  
- Domain Context: Include relevant technical documentation

---

## 📈 Performance Comparison

| Method              | Compilation Success | Integration Quality | Code Accuracy | Time Efficiency |
|---------------------|--------------------|--------------------|---------------|-----------------|
| Zero-Shot           | ✅ High             | ❌ Poor            | ✅ Good       | ✅ Excellent     |
| Role-Based          | ✅ High             | ✅ Excellent        | ⚠️ Partial    | ❌ Poor         |
| Few-Shot            | ❌ Failed           | ⚠️ Moderate         | ✅ Good       | ✅ Good         |
| Chain-of-Thought    | ❌ Failed           | ❌ Poor             | ⚠️ Moderate   | ✅ Good         |
| Iterative Refinement| ❌ Failed           | ⚠️ Moderate         | ✅ Good       | ⚠️ Moderate     |
| Template-Based      | ✅ High             | ⚠️ Moderate         | ✅ Excellent  | ✅ Good         |

---

## 🔮 Future Work

### Immediate Next Steps

- Develop agentic LLM systems for autonomous testing and correction  
- Implement LLM-assisted validation and testing frameworks  
- Use LLMs for identifying and optimizing performance bottlenecks

### Long-term Research Directions

- Fine-tune domain-specific LLMs on architectural simulation codebases  
- Improve context management for large codebases and documentation  
- Extend to multi-simulator support (gem5, Ramulator, etc.)  
- Establish best practices for human-LLM collaborative workflows

### Experimental Extensions

- Explore multi-agent and tool-augmented prompting  
- Extend methodology across languages and architectures  
- Develop benchmarking metrics for LLM code generation quality

---

## 📚 References

- VANS Simulator - Base heterogeneous memory simulator  
- CXLMemSim - Reference CXL memory simulator  
- CXLMemSim Paper - Technical background on CXL memory simulation  
- Prompt Engineering Guide - Reference on prompting techniques  

