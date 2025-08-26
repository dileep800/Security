Western Union ServiceNow – When Configs Go Rogue

Not every bug bounty win comes from clever payloads or fuzzers. Sometimes, it’s the quiet misconfigurations that spill the most secrets. That’s exactly what happened with Western Union’s ServiceNow instance.

🕵️ Recon

During recon, I came across:

https://westernunionlaca.service-now.com/

!Image images/westernunion.png
ServiceNow portals are always worth checking because they often tie into customer service and internal ops.

🚀 The Weak Spot
!Image2 images/westerunion2.png
I tested a few weak credentials on the exposed login. To my surprise, one worked — giving me more access than I should have had.

Inside, I could query endpoints and pull sensitive data.

!Image3 images/westernunion3.png
⚡ Impact

📂 Customer support tickets exposed

🕵️ Internal system logs accessible

⚠️ Potential leakage of PII and business processes

For a financial services company, this could be devastating in the wrong hands.

🛡️ Remediation

Disable default/weak accounts.

Apply strict least-privilege access.

Monitor third-party SaaS configs with the same rigor as in-house apps.

🎯 Takeaway

Sometimes the weakest link isn’t custom code — it’s an overlooked SaaS platform. This was a good reminder that security isn’t just about code reviews, it’s about configurations too.
