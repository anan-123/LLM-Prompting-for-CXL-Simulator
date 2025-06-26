# LLM-Prompting-for-CXL-Simulator

Extending architectural simulators for emerging memory technologies using Large Language Models (LLMs)

---

## Project Overview

This research project explores the feasibility of using Large Language Models (LLMs), such as ChatGPT and Claude, to extend the VANS (Validated cycle-Accurate NVRAM Simulator) with support for CXL (Compute Express Link) memory simulation. Unlike traditional manual development, this work employs prompt engineering techniques to generate the required code components automatically.

**Objective:**  
Develop a CXL-capable version of the VANS simulator by using LLMs to automate the extension process rather than building from scratch.

---

## Research Questions

- Can LLMs effectively extend complex architectural simulators?
- Which prompting techniques work best for systems-level code generation?
- What are the capabilities and limitations of AI-assisted simulator development?
- How does LLM-generated code compare to traditionally developed code?

---

## Architecture

### Base Technologies

- **VANS Simulator:** Modular, event-driven, cycle-accurate simulator for Optane DIMM-based systems
- **CXL Memory:** Compute Express Link (CXL) memory model for shared memory access across CPUs
- **LLMs Used:** GPT-4 Turbo and Claude 3.5 Sonnet for prompt-based code generation

### Core Components Generated
```
src/
├── cxl_memory.cpp # CXL Type 3 memory device implementation
├── cxl_memory.h # Header file for CXL memory model
├── cxl_system.cpp # Request routing and CXL system control
├── cxl_system.h # Header for CXL system logic
├── factory.cpp # Factory pattern extension for CXL support
├── vans.cpp # Core integration of VANS with CXL modules
└── config/
└── cxl_config.cfg # Configuration parameters specific to CXL simulation

```
### System Integration Strategy

- **Modular Design:** Preserves the structure of VANS
- **Factory Pattern:** Supports runtime configurability for CXL memory devices
- **Event-Driven Simulation:** Maintains cycle-accurate performance modeling
- **Hybrid Memory Hierarchy:** Enables simulation of systems with both DRAM and CXL-attached memory

---

## Methodology

The project tests various prompt engineering strategies to generate and refine simulator code using LLMs:

### Prompting Techniques

- **Zero-Shot Prompting:** One-shot prompt with full context but no prior interaction
- **Role-Based Prompting:** Assigns system roles to LLMs and provides detailed file structure
- **Few-Shot Learning:** Supplies example code to guide generation
- **Chain-of-Thought (CoT):** Breaks down complex tasks into smaller logical steps
- **Iterative Refinement:** Generates and improves code through multiple feedback cycles

---

## Experimental Results

### Performance Metrics

| Access Pattern | DRAM Utilization | Latency / Operations      |
|----------------|------------------|----------------------------|
| Sequential     | 82.81%           | 92.03 ns                   |
| Hotspot        | 80.04%           | 200,000 operations         |
| Random         | 64.03%           | 250,000 operations         |

- Performance improved by up to 15.04% in optimized configurations

### LLM Evaluation

- Average Token Usage: ~1000 tokens per session
- Generation Time: Few seconds to minutes per iteration
- Refinement Cycles: Typically 2–3 iterations per module
- Success Rate: Dependent on prompting strategy and task complexity

---

## Key Findings

### Strengths

- Fast generation of boilerplate and modular code
- High-quality documentation and code readability
- Effective debugging assistance
- Clear architectural planning and integration guidance

### Limitations

- Struggles with deep system-level interactions
- Needs explicit context and domain-specific details
- Requires guidance on project file structure
- Limited optimization capabilities
- Potential for error propagation without validation

### Best Practices

- Clearly define the architecture and file layout in prompts
- Use a combination of prompting strategies
- Validate outputs early through testing
- Provide technical documentation as part of context
- Apply iterative refinement for higher-quality results

---

## Performance Comparison

| Method               | Compilation Success | Integration Quality | Code Accuracy | Time Efficiency |
|----------------------|---------------------|----------------------|----------------|------------------|
| Zero-Shot            | High                | Poor                 | Good           | Excellent        |
| Role-Based           | High                | Excellent            | Partial        | Poor             |
| Few-Shot             | Failed              | Moderate             | Good           | Good             |
| Chain-of-Thought     | Failed              | Poor                 | Moderate       | Good             |
| Iterative Refinement | Failed              | Moderate             | Good           | Moderate         |
| Template-Based       | High                | Moderate             | Excellent      | Good             |

---

## Future Work

### Short-Term Goals

- Build self-correcting LLM agents for autonomous testing
- Introduce LLM-based verification and regression testing
- Explore performance tuning through AI-assisted code optimization

### Long-Term Research Directions

- Fine-tune domain-specific LLMs on simulation codebases
- Improve context handling for large architectural projects
- Extend the methodology to other simulators such as gem5 and Ramulator
- Formalize hybrid development workflows involving both humans and LLMs

### Experimental Extensions

- Implement multi-agent prompting systems
- Apply this approach to additional programming languages and hardware models
- Define benchmark metrics for evaluating LLM-based code generation

---

## References

- VANS Simulator: Base heterogeneous memory simulation platform
- CXLMemSim: Reference implementation for CXL simulation
- CXLMemSim Technical Paper: Background on CXL system-level modeling
- Prompt Engineering
