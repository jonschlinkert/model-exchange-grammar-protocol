# MEGP

[Model Exchange Grammar Protocol](grammar.md)

## Objectives

The Model Exchange Grammar Protocol aims to be a simple, extensible, and non-deterministic grammar for specifying valid message types and their arrangements in exchanges with language models. While various interaction patterns exist across different AI systems and applications, this protocol aims to standardize the expected behavior and provide clear guidance for implementing structured model interactions.

The MEGP specification is a work in progress, you can view the document in its current state [here](grammar.md).

## Example Usage

A typical exchange might be defined as:

```
<exchange> ::= (<turn>)*
<turn> ::= <role_message>
<role_message> ::= <system_message> | <user_message> | <assistant_message> | <tool_message>
<system_message> ::= <message>
<user_message> ::= <message>
<assistant_message> ::= <message>
<tool_message> ::= <message>
```

## Why is this needed?

When designing AI-powered interfaces, debugging conversation flows, or explaining expected behavior in code and documentation, developers need a clear way to model and communicate interaction patterns. Common challenges include:

- **Designing new interfaces** - How do you specify what message types are valid and in what order?
- **Code documentation** - How do you clearly explain the expected conversation flow in comments or specs?
- **Bug reports and discussions** - How do you precisely describe what should happen vs. what actually happened?
- **Refactoring conversation logic** - How do you ensure your changes preserve the intended interaction patterns?
- **Onboarding team members** - How do you quickly communicate complex multimodal interaction flows?

The Model Exchange Grammar Protocol provides a concise, formal notation for these scenarios. Instead of lengthy prose or ambiguous examples, you can write:

```
<user_message> ::= <text> [<image>]
<exchange> ::= <user_message> <assistant_message> [<tool_message> <assistant_message>]
```

This enables:

- **Clear interface design** with unambiguous interaction patterns
- **Precise documentation** that's both human-readable and formally specified
- **Better bug reports** with exact descriptions of expected vs. actual behavior
- **Confident refactoring** with formal validation of conversation logic
- **Faster onboarding** through concise, standardized interaction descriptions

## Contributing

[Contributions](contributing.md) are always welcome and appreciated!

You can contribute to the development of this protocol by submitting a [pull request](../../pulls), opening [an issue](../../issues), or joining us in [the discussions](../../discussions).
