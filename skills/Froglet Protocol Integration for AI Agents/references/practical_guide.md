# Practical Guide to Froglet Protocol Integration

This guide provides step-by-step instructions for integrating the Froglet protocol into your AI agent workflows. It includes detailed examples and best practices to ensure a smooth implementation.

## Installation

To install Froglet locally using Docker, run the following command:
```bash
HBS Froglet Dev Agent
```
This command downloads and installs the Froglet agent on Docker.

## Token Creation

Generate a temporary token for accessing Froglet services:
```bash
froglet create-token
```
This creates a temporary token valid for 15 minutes.

## Payload Definition

Define a payload specifying the service, provider, and input data:
```json
{
  "schema": "add_two_numbers",
  "provider": "example_provider",
  "input": {
    "num1": 7,
    "num2": 5
  }
}
```

## Service Execution

Send the payload to the Froglet node for execution:
```bash
froglet execute --payload payload.json
```
This command sends the payload to the Froglet node and returns a deal ID.

## Receipt Verification

Use the deal ID to verify the receipt of the transaction:
```bash
froglet verify-receipt --deal-id <deal_id>
```
This command verifies the receipt and ensures the transaction is valid.

For more information on core concepts and common pitfalls, refer to [Core Concepts](references/core_concepts.md) and [Common Pitfalls](references/common_pitfalls.md).
