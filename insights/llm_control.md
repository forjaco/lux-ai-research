# LLM Control

In the private system, language models do not decide behavior. They can only render language inside constraints defined by the simulation stack.

That design choice matters because it keeps:
- intent under system control
- state transitions deterministic
- fallback available when generated language drifts
- behavioral safety separate from text fluency

This repository discusses the principle, but does not expose the internal prompts, validators, or routing policies in full.
