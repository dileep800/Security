Cisco Reflected XSS – When Redirects Get Sassy

Bug hunting often feels like panning for gold — you sift through a lot of dirt before you find the shiny stuff. This time, the shiny thing was hiding inside a redirect parameter on Cisco’s bgpmon.net login portal.

🕵️ Recon

The endpoint looked like this:

https://portal.bgpmon.net/loginCheck.php
!Image images/ciscoxss.png

Burp Suite showed me a juicy parameter: return_url. Anyone who’s hunted before knows this parameter is basically an invitation to mischief.

🚀 The Payload

I tried the good old classic:

<script>alert(1)</script>

!Image2 images/ciscoxss2.png
Reloaded the page… and there it was. My little JavaScript popped up like fireworks on the 4th of July.

Reflected XSS confirmed.

⚡ Why It’s Dangerous

It’s “just an alert box,” right? Not quite. On a login page, this meant:

🍪 Stealing session cookies

🎣 Injecting fake login forms

💀 Redirecting users to malicious domains

Suddenly that tiny alert box looks a lot scarier.

🛡️ Remediation

Sanitize inputs (always).

Encode outputs (especially in URLs).

Throw in a solid CSP to stop inline scripts.

🎯 Takeaway

Even in 2025, the classics still work. Reflected XSS is old-school, but when it shows up on a login portal of a major vendor, it’s no joke. Sometimes the “boring” bugs are the ones that matter most.
