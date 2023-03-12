---
layout: page
title: ggVerify
description: An email-based verification service for the GGPen Discord server.
noindex: true
---

ggVerify is an email-based verification service for the GGPen Discord server, an unofficial server for DigiPen Singapore students and alumni.

<style>
    #redirect-pane{
        margin: 4rem auto;
        padding: 1rem;
        padding-bottom: 0;
        border: 1px dotted currentColor;
        border-radius: 1rem;
    }
</style>
<script>
    "use strict";
    const url = new URL(document.URL);
    const regex = RegExp("(GGPEN-[0-9a-f]+)");
    const results = regex.exec(url.search);
    if(results != null && results.length > 0)
    {
        document.write("<div id='redirect-pane'></div>");
        const code = results[0];
        const redirect = `mailto:ggverify@dangeraspect.xyz?subject=${encodeURIComponent("GGPen verification: ")}${code}&body=${encodeURIComponent("Please check that you are sending this from your institutional email address!\n\nFor details, see https://dangeraspect.xyz/ggverify/.\n-----")}`;
        document.getElementById('redirect-pane').innerHTML = `<p><strong>Your email client should open automatically</strong> with the subject and recipient filled in. If not, <a href="${redirect}">click here to open in your default email client</a>.</p>`;
        window.onload = function(){window.location = redirect;}
    }
</script>

## How it works

On the GGPen Discord server, run the `/verify` command. 

Instructions will be provided along with a unique verification code. Send an email from your institutional email address to the given email address with the verification code as the subject line. That's all!

Behind the scenes, ggVerify is written in JavaScript and run on Cloudflare Workers. The source code is available at [TBA](#).


## Privacy

**What data is collected**: In summary, ggVerify collects and links your Discord user ID with your provided institutional email adress. This service is controlled by [Joey](https://joeyfoo.com/contact).

**How is your data stored**: This data is stored using Cloudflare Workers KV, on an account managed by Joey. Your numeric Discord ID and provided email address is stored. 

**How is your data used**: This data may be used for server moderation purposes, and may be provided to server mods, and/or SIT or DP staff, if needed. 

This is similar to existing server rules, which already require that all members indicate their real identities in their server nickname. Verification serves simply as an additional layer of assurance.

**Your data rights**: Your data can be deleted at any time by running the `/verify` command again, and clicking on the `Unverify` button. Data is deleted within 60 seconds, and no data is retained.

