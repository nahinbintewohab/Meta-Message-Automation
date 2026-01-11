# Meta Message Automation - n8n Workflow

An intelligent AI-powered customer service chatbot for Revencomm that automatically responds to Facebook Messenger messages using OpenAI's GPT-4o-mini model.

## Overview

This n8n workflow creates an automated messaging system that handles customer inquiries about Revencomm's services through Facebook Messenger. The bot is specifically trained to provide information about the company's digital marketing and business solutions.

## Features

- **AI-Powered Responses**: Uses OpenAI GPT-4o-mini for natural, context-aware conversations
- **Memory Management**: Maintains conversation history (15 message window) for contextual responses
- **Service-Focused**: Specialized responses about Revencomm's 6 core services
- **Webhook Verification**: Handles Facebook webhook verification automatically
- **Human-like Responses**: Configured to provide concise, natural replies (15 words max)

## Revencomm Services Covered

1. Brand Promotion
2. Business Analysis
3. Graphics Design
4. Data-Driven Digital Marketing
5. Customer Tracking
6. Web Development

## Workflow Architecture

### Nodes

1. **Webhook** - Receives incoming Facebook Messenger messages
2. **If** - Verifies webhook subscription with verification token
3. **Respond to Webhook** - Returns challenge for webhook verification
4. **AI Agent** - Processes messages and generates responses
5. **OpenAI Chat Model** - GPT-4o-mini integration
6. **Simple Memory** - Maintains conversation context
7. **Call n8n Workflow Tool** - (Optional) Web scraping capability
8. **Code** - Formats response for Facebook Messenger API
9. **HTTP Request** - Sends response back to Facebook Messenger

## Setup Instructions

### Prerequisites

- n8n instance (self-hosted or cloud)
- OpenAI API key
- Facebook Page and App
- Facebook Page Access Token

### Configuration Steps

1. **Import Workflow**
   - Import the `meta_message_automation.json` file into your n8n instance

2. **Configure OpenAI Credentials**
   - Add your OpenAI API credentials
   - Model: gpt-4o-mini

3. **Set Facebook Webhook**
   - Webhook URL: `https://your-n8n-instance.com/webhook/message-handler`
   - Verify Token: `diba-message`
   - Subscribe to `messages` events

4. **Update Facebook Access Token**
   - Replace the access token in the HTTP Request node
   - Update the Page ID in the API URL

5. **Activate Workflow**
   - Enable the workflow in n8n

## Configuration Details

### Webhook Verification

```
Verification Token: diba-message
Hub Mode: subscribe
```

### Facebook API Endpoint

```
POST https://graph.facebook.com/v23.0/{PAGE_ID}/messages
```

### AI Agent System Prompt

The AI agent is configured with:
- Strict service-focused responses
- Professional tone
- 15-word maximum responses
- No special characters (*, bullets)
- Natural, human-like language

### Memory Configuration

- Session Key: Facebook Sender ID
- Context Window: 15 messages
- Type: Buffer Window Memory

## Response Behavior

The bot will:
- Introduce itself with available services
- Answer questions about Revencomm's offerings
- Redirect off-topic questions professionally
- Keep responses under 15 words
- Maintain conversation context

The bot will NOT:
- Provide general business advice unrelated to services
- Discuss competitors
- Handle casual conversation
- Provide technical support for non-Revencomm products

## Example Interactions

**Customer**: "What services do you offer?"

**Bot**: "We offer Brand Promotion, Business Analysis, Graphics Design, Digital Marketing, Customer Tracking and Web Development."

**Customer**: "Tell me about your web development"

**Bot**: "We build dynamic websites that convert visitors into clients with optimized design and functionality."

## Troubleshooting

### Webhook Not Receiving Messages

- Verify webhook URL is accessible publicly
- Check verification token matches in Facebook App settings
- Ensure workflow is active

### AI Not Responding

- Check OpenAI API credentials
- Verify API quota/limits
- Review n8n execution logs

### Facebook API Errors

- Verify Page Access Token is valid and not expired
- Check Page ID is correct
- Ensure app has necessary permissions

## Security Considerations

- Store access tokens securely using n8n credentials
- Regularly rotate Facebook access tokens
- Monitor API usage and rate limits
- Review webhook security settings

## Customization

### Modify Services

Edit the system prompt in the AI Agent node to update:
- Service descriptions
- Company information
- Response guidelines
- Tone and style

### Adjust Response Length

Change the word limit in the system prompt:
```
your reply must be short in [N] words only
```

### Update Memory Window

Modify `contextWindowLength` in Simple Memory node to increase/decrease context retention.

## API Versions

- Facebook Graph API: v23.0
- n8n nodes: Latest compatible versions
- OpenAI Model: gpt-4o-mini

## Maintenance

- Regularly update Facebook access tokens
- Monitor OpenAI API usage and costs
- Review conversation logs for quality
- Update service information as needed

## Support

For issues or questions:
- Check n8n execution logs
- Review Facebook webhook logs
- Verify OpenAI API status
- Contact Revencomm technical team

---

**Last Updated**: January 2026  
**Workflow ID**: mt5FkudeBcY34836  
**Version**: 1.0
