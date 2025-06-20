# Model Exchange Grammar Protocol

## Introduction

The Model Exchange Grammar Protocol defines a simple, extensible, and non-deterministic grammar for specifying valid message types and their arrangements in exchanges with language models. This protocol enables precise, unambiguous specification of interactions including multimodal content, tool calls, and flexible message sequencing.

## 1. Notation

The protocol uses a BNF-like notation, with the following symbols:

| Symbol   | Description                       |
| -------- | --------------------------------- |
| `<A>`    | Non-terminal (named symbol/rule)  |
| `"text"` | Literal value or keyword          |
| `\|`     | Alternatives (logical OR)         |
| `[]`     | Optional (zero or one occurrence) |
| `{}`     | Zero or more repetitions          |
| `()`     | Grouping of rules                 |
| `+`      | One or more repetitions           |
| `*`      | Zero or more repetitions          |

## 2. Message Modalities

A message can contain one or more of the following content blocks:

- text
- image
- audio
- video
- tool_call

Additional modalities may be defined as needed.

## 3. Basic Message Form

Basic message types are defined as follows:

```
<message> ::= <content_block>+
<content_block> ::= <text> | <image> | <audio> | <video> | <tool_call>
```

- `+` indicates one or more content blocks can be combined in a single message.

## 4. Message Roles

Messages are produced by different roles:

- system
- user
- assistant
- tool

Each message is associated with a single role. The sequence and alternation of message roles can be defined according to the protocol needs.

## 5. Message Sequences (Exchanges)

A typical exchange is defined as:

```
<exchange> ::= (<turn>)*
<turn> ::= <role_message>
<role_message> ::= <system_message> | <user_message> | <assistant_message> | <tool_message>
<system_message> ::= <message>
<user_message> ::= <message>
<assistant_message> ::= <message>
<tool_message> ::= <message>
```

## 6. Tool Calls and Function Calls

The protocol supports tool/function call semantics:

```
<assistant_message> ::= <message> [<tool_call>]
<tool_call> ::= "tool_call" <tool_spec>
<tool_spec> ::= <tool_name> <tool_args>
<tool_name> ::= "string"
<tool_args> ::= "json_object"
```

A tool call is optionally followed by further assistant or user messages, depending on the application logic.

## 7. Multimodal and Composite Messages

To specify messages combining multiple modalities:

```
<message> ::= <text> [<image>] [<audio>] [<video>] [<tool_call>]
```

or to allow multiple blocks of each kind:

```
<message> ::= {<content_block>}
```

## 8. Optional Metadata

Messages may include optional metadata blocks.

```
<message> ::= <content_block>+ [<metadata>]
<metadata> ::= "key:value" {"," "key:value"}
```

## 9. Example Protocols

### Text-Only Chat

```
<message> ::= <text>
<exchange> ::= (<user_message> <assistant_message>)+
```

### Multimodal Assistant Interaction

```
<message> ::= <text> [<image>] [<audio>] [<tool_call>]
<exchange> ::= (<system_message> | <user_message>)+ <assistant_message>*
```

### Tool Call with Result

```
<exchange> ::= <user_message> <assistant_message> <tool_message> <assistant_message>
```

## 10. Extensibility

- Additional roles or content types can be added by extending the non-terminals.
- Tool/function call structures can be customized as needed.
- Metadata keys/values are open-ended for application-specific use.

## 11. Conformance

A "Model Exchange Grammar" document is considered conformant if:

1. It adheres to the BNF-like notation described here.
2. It describes all message types, roles, and permissible sequences for a particular interaction pattern.

## 12. References

This protocol draws on principles from Backus–Naur Form (BNF), augmented for modeling in model-based exchanges.

_End of Model Exchange Grammar Protocol_
