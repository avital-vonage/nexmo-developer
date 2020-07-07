---
title: Message Privacy
---

# Message Privacy

Vonage provides two solutions to cover your compliance and privacy needs. The Auto-redact service and the Redact API allow you to redact sensitive or personal information either automatically or on demand from our platform.

## Stored data and redaction

![Advanced SMS Redaction](/assets/images/messaging/sms/advanced_sms_redaction.png)

When using any Vonage communication APIs two forms of logging are created. Server logs get created as are transactional records of the activity known as a Call Detail Record (CDR). Server logs are retained for around 15 days, no more than one month. CDRs however are stored for 13 months. Both server logs and CDRs are viewable by Vonage support staff, for testing, debugging, diagnosing user issues and reconciling CDRs against customer's transaction records.

Personal Identifiable Information (PII) stored in the Vonage platform can be removed using the Auto-redact service and the Redact API. PII generally includes the receiver phone number for outbound messages, or calls and the sender phone number for inbound messages. PII also includes the message content of the SMS messages.

When redacted, the real PII content in the redacted fields is overwritten with the string "REDACTED". 

Upon redaction, the real PII content in the redacted fields is overwritten with the string "REDACTED". The phone number of both the receiver and senders are subject to applicable data retention regulations specific to the country that phone number belongs to.

Customers can view the redacted CDRs using either the Reports API or the Customer Dashboard.

## Detailed description of redaction scope for SMS API

Feature | Description
----|----
PII | PII includes the message content and the receiver phone number for outbound messages and the sender phone number for inbound messages. The SMS API uses a data pipeline software to transport CDRs to various databases. The data pipeline keeps CDRs along with the receiver/sender phone number for 7 days. Thus, besides server logs and the long-term storage of CDRs, PII is also stored in the data pipeline logs.
Supported Auto&#8209;redact type | Advanced
Auto&#8209;redact details | Advanced Auto-redact for SMS redacts server logs, CDRs, and the data pipeline logs. The scope of auto-redaction is configurable and can include the following options:<p>1. Message content redaction only.<br/> 2. Phone number redaction only.<br/> 3. Phone number encryption only.<br/> 4. Message content redaction together with redaction or encryption of the phone number.</p>When immediate message content redaction is configured, message content is not written at all, not even to the server logs or the data pipeline logs. When number redaction is configured, the phone number gets encrypted by the SMS API before it gets written to the server logs and the data pipeline logs. When CDRs get propagated to the long-term storage of CDRs, the encrypted number field gets automatically redacted. The logs containing encrypted numbers expire on their own. **Neither Support or any other Vonage personnel have access to decryption keys.**
Redact API details | Redact API redacts only the CDRs in the long-term storage of CDRs. The scope of redaction is not configurable and includes message content together with the phone number.

## Benefits

Feature | Description
----|----
Latency | Advanced auto-redact with Nexmo does not store content of message bodies as well as phone numbers. From the time of entry this information is redacted. Other providers may store sensitive information for a length of time prior to redaction.
Configuration | Account-level configuration is made by one of the support team as this functionality isn't available in the customer dashboard.
Redaction scope | The phone number is encrypted from the start and then redacted in CDRs. CDRs contain only the routing prefix. Other providers may only obfuscate the last four digits of a phone number in the message request.
MMS | Redaction for MMS is not covered under the SMS redaction, but instead under the [Messages API](https://developer.nexmo.com/redact/overview#messages-api)
Inbound and Outbound SMS | Advanced auto-redact applies for outbound SMS messages. Inbound SMS messages are covered with the standard auto-redact functionality.
Legislation | Due to data retention legislation of various EU countries, the phone number may be retained depending on which country the number belongs to. The message body however is not retained.


## Instruction

Please find a relevant pricing for the auto-redact service here: [Vonage Prices](https://www.vonage.com/communications-apis/pricing/).

To request activation of the Auto-redact service for your account, please visit [this page](https://info.nexmo.com/RedactAPI.html).


