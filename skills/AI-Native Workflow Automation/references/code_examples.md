# Code Examples and Prompt Templates

## Basic Skill File Template
```markdown
# Skill: Process Customer Refund

## Purpose
Handle customer refund requests according to company policy

## Inputs
- Customer email or ticket
- Order details
- Reason for refund

## Steps
1. Verify order meets refund policy criteria
2. Calculate refund amount
3. Approve with manager if over $100
4. Process payment system update
5. Send customer confirmation

## Outputs
- Updated order status
- Refund transaction record
- Customer notification
```

## Resolver Table Example
```typescript
const resolverTable = {
  "customer_refund": "skills/process_refund.md",
  "invoice_processing": "skills/process_invoice.md",
  "technical_support": "skills/handle_support_ticket.md",
  "default": "skills/escalate_to_human.md"
};

function routeTask(taskType) {
  return resolverTable[taskType] || resolverTable.default;
}
```

## Context Engineering Prompt
```
You are an AI assistant with access to our company brain. Before responding to this customer request, please:

1. Retrieve all prior interactions with this customer
2. Find 3 similar cases and their resolutions
3. Review current policies related to this request
4. Synthesize this information before formulating your response

The request is: [PASTE REQUEST HERE]
```

## Skillification Prompt
```
I just completed this task successfully:
[TASK DESCRIPTION]

Please convert this into a reusable skill file with:
1. Clear purpose statement
2. Defined inputs
3. Step-by-step instructions
4. Expected outputs
5. Any relevant policy references

Format as markdown ready to add to our skills directory.
```