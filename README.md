# Auto-Poster & Mobile Trigger

This is a setup I built using Make.com and GPT-4o to handle social media posts automatically. It basically watches a folder, figures out what's in the photo using AI, and posts it to multiple platforms so I don't have to.

I also added a mobile trigger so I can force a post to go live just by hitting a button on my iPhone.
How it works

There are two main parts to this:
1. The Auto-Post Scenario
This one runs on a schedule. It checks a cloud folder, and if it finds a new image, it:
    Sends a preview to Discord (just so I can keep track).
    Runs the image through GPT-4o to write a caption. I spent a while tuning the prompt so the AI sounds natural and identifies specific details in the photo.
    Uses a Router to push the post to Instagram and Facebook at the same time.
    Deletes the file from the folder once it’s done to keep things clean.

2. The iOS Shortcut (Manual Override)
I wanted a way to trigger the whole process instantly from my phone.
    I used the Make iOS integration to create a button trigger.
    When I press it, my phone sends a notification saying "Starting posting process."
    It calls the main posting scenario as a "Sub-scenario" (keeping the logic modular).
    Once the API confirms the upload, I get another ping on my phone saying it’s live.

Tech Used:
    Make.com for the logic/workflow.
    OpenAI API for the computer vision and captions.
    Discord Webhooks for logging.
    Social Graph APIs (IG & FB).

Why I built it this way
Instead of just making one long, messy workflow, I split them up. By using a Sub-scenario, I can trigger the posting logic from anywhere—whether it's a folder update, a mobile button, or a webhook—without rebuilding the same steps over and over.
