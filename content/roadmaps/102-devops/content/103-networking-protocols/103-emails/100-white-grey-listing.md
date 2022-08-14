# White grey listing
#
#Greylisting is a method of defending e-mail users against spam. A mail transfer agent (MTA) using greylisting will #"temporarily reject" any email from a sender it does not recognize. If the mail is legitimate, the originating server will try again after a delay, and if sufficient time has elapsed, the email will be accepted.
#
# How it works
#


A server employing greylisting temporarily rejects email from unknown or suspicious sources by sending 4xx reply codes ("please call back later"), as defined in the Simple Mail Transfer Protocol (SMTP). Fully capable SMTP implementations are expected to maintain queues for retrying message transmissions in such cases, and so while legitimate mail may be delayed, it should still get through.

The temporary rejection can be issued at different stages of the SMTP dialogue, allowing an implementation to store more or less data about the incoming message. The trade-off is more work and bandwidth for more exact matching of retries with original messages. Rejecting a message after its content has been received allows the server to store a choice of headers and/or a hash of the message body.

In addition to whitelisting good senders, a greylister can provide for exceptions. Greylisting can generally be overridden by a fully validated TLS connection with a matching certificate. Because large senders often have a pool of machines that can send (and resend) email, IP addresses that have the most-significant 24 bits (/24) the same are treated as equivalent, or in some cases SPF records are used to determine the sending pool. Similarly, some e-mail systems use unique per-message return-paths, for example variable envelope return path (VERP) for mailing lists, Sender Rewriting Scheme for forwarded e-mail, Bounce Address Tag Validation for backscatter protection, etc. If an exact match on the sender address is required, every e-mail from such systems will be delayed. Some greylisting systems try to avoid this delay by eliminating the variable parts of the VERP by using only the sender domain and the beginning of the local-part of the sender address.
