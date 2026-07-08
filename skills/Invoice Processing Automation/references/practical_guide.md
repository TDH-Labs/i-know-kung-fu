# Practical Implementation Guide

## Environment Setup
1. Create a dedicated Gmail filter for incoming invoices
2. Set up a Cloud Code project with necessary permissions
3. Configure QuickBooks Online developer access
4. Create a Slack channel for notifications

## Native Integration Approach
### Step 1: Gmail Trigger
```javascript
// Cloud Code function to monitor Gmail
function checkIncomingEmails() {
  const query = 'label:invoices is:unread';
  const threads = GmailApp.search(query);
  threads.forEach(processInvoiceThread);
}
```

### Step 2: Invoice Processing
```javascript
function processInvoiceThread(thread) {
  const messages = thread.getMessages();
  const attachments = messages[0].getAttachments();
  const pdfText = extractTextFromPDF(attachments[0]);
  
  // Extract key fields using regex
  const vendor = pdfText.match(/Vendor:\s*(.+)/)[1];
  const amount = parseFloat(pdfText.match(/Total:\s*\$?([\d,]+\.[\d]{2})/)[1]);
  
  return { vendor, amount };
}
```

## Zapier Integration Approach
1. Create Zapier account and connect all services
2. Set up trigger: "New email in Gmail with invoice label"
3. Add action: "Extract data from PDF"
4. Add action: "Create bill in QuickBooks"
5. Add action: "Post notification to Slack"

## Error Handling
- Implement retry logic for failed API calls
- Create dead-letter queue for unprocessable invoices
- Set up alerts for repeated failures