Recreation.gov Open Redirect – When Trust Can Be Misused

I was poking around Recreation.gov, the government portal for parks and activities, when I noticed something curious in their URL flow. There was a parameter called url in the redirect endpoint. For bug hunters, that’s like a neon sign flashing: “Test me!”.

The original link looked totally innocent:

https://www.recreation.gov/api/redirect?account_id=32dd40e4-07fa-5832-adb6-e94b3d1a05e5&url=https://www.bugcrowd.com


Redirect parameters are meant to send users back to where they came from, usually after login or some action. But if the app doesn’t validate them properly, you can make users go anywhere you want.

🚀 Testing the waters

I swapped the url value with a domain I control:

https://www.recreation.gov/api/redirect?account_id=32dd40e4-07fa-5832-adb6-e94b3d1a05e5&url=https://evil.com

!Image images/OPEN20VULN20SITE!!!!.mp4
Hit enter… and boom 💥. The site redirected me straight to evil.com, no questions asked.

That little moment—when a tiny tweak shows the site trusts your input a bit too much—is always satisfying.

⚡ Why this matters

Some might say Open Redirects are “low severity,” but on a government site, it’s different. Combine this with social engineering and you’ve got a powerful phishing attack:

Send a link from Recreation.gov to a user.

They click it thinking it’s legitimate.

Behind the scenes, they land on a fake page designed to steal credentials.

It’s the classic wolf in sheep’s clothing scenario.

🛡️ How to fix it

Fixing this isn’t rocket science, but it’s crucial:

Validate redirect URLs against a whitelist of approved domains.

Never trust external values blindly when redirecting.

Sanitize inputs before processing them.

🎯 Takeaway

Even “simple” bugs like Open Redirects can be dangerous when paired with phishing. Government websites carry extra trust weight, so every parameter deserves a second look.

This one reminded me that responsible disclosure matters—report it, let the team fix it, and teach others safely.

Dileep Chowdary
