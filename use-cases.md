# Use Cases

Our goal is to establish this grammar as a shared vocabulary for talking about AI interactions precisely. Use this document as inspiration for when to use this grammar.

## System Design & Research

- **Prompt engineering docs** - Clearly specify which prompt patterns work for different interaction types
- **Model behavior analysis** - Formally describe what you expected vs. what the model actually did
- **A/B testing conversation flows** - Define variants precisely for experimentation
- **Training data specification** - Describe the exact conversation patterns you want in datasets

## Team Communication

- **Feature requirements** - "The chatbot should handle this exact flow: `<user_message> ::= <text> | (<text> <image>)`"
- **Code reviews** - Quickly verify that implementation matches intended conversation logic
- **Architecture discussions** - Debate different interaction patterns using precise notation
- **Cross-team handoffs** - Frontend/backend teams can agree on exact message structures

## AI Product Development

- **Edge case specification** - Define exactly when tool calls should trigger, when they shouldn't
- **Multimodal interaction design** - Plan complex flows mixing text, images, audio before building
- **Error handling patterns** - Specify what happens when expected message types don't appear
- **User journey mapping** - Model entire conversation trees with branching paths

## Community & Open Source

- **GitHub issue templates** - "Expected behavior: `<grammar here>`, Actual behavior: `<different grammar>`"
- **API documentation** - Replace verbose examples with concise, complete grammar definitions
- **Tutorial creation** - Show learners exactly what conversation patterns are possible
- **Standards discussions** - Debate AI interaction patterns using shared formal language
