# THE AGILE99 SIMPLE RULES
**Print this. Pin it. Read it before every session.**

---

## A Feature in Five
Five chats. Five branches. One shipped feature.
Every feature. Every time.

```
Chat 1 PLAN    → Oracle the Organizer    (max 20 prompts)
Chat 2 BUILD   → The Architect           (max 30 prompts)  
Chat 3 CODE    → Cypher the Coder        (max 40 prompts)
Chat 4 QA+FIX  → Trinity the Tester     (max 40 prompts)
Chat 5 PROMOTE → Tank the Transporter   (max 20 prompts)
UAT            → You (The One)
```

---

## The 10 Simple Rules (Catchy Edition)

**1. Prompt 21 is Done.**
Maximum 20 prompts per chat. Hit 21? Close the chat, open a new one, paste the opener. The files carry the context -- not the chat.

**2. New Branch. New Name.**
One branch = one phase = one persona = one role. When the phase changes, the chat closes, the branch closes, the persona changes. Always.

**3. Read Before You Write.**
Agent reads AI_RULES.md + CONTEXT.md before writing a single line of code. No confirmation = stop and ask for it.

**4. Plan Before You Build.**
No code without an approved plan. The Architect does not build what Oracle has not approved.

**5. One Thing. One Prompt.**
Never ask for two things in one prompt. "And also..." is a second prompt. Send it separately.

**6. Show Don't Describe.**
Screenshot + console error + Vercel log. Never describe a bug in prose when you can show it. Trinity fixes bugs 3x faster with all three pieces of evidence.

**7. Main is Sacred.**
Never push directly to main. PRs only. Branch protection is on. This is not optional.

**8. Close the Chat, Not the Tab.**
Run the End of Chat Protocol before closing any chat. The files need updating. The system needs to improve. Five minutes now saves hours next session.

**9. When in Doubt, Audit.**
Messy codebase? Call Smith before Cypher. Audit before features. Debt compounds.

**10. Wake Up, Neo.**
You are The One. UAT is yours. No agent can test it for you. Open the staging URL. Use it as a real user. If it feels wrong -- it is wrong.

---

## The 8S Standard
Every feature should move the codebase closer to all 8:

**Swift. Simple. Stable. Secure. Scalable. SaaS-Ready. Sellable. Supportable.**

---

## The 3-Minute Rule
Always wait 3 minutes after pushing to staging before testing.
Vercel needs time. Testing too early = testing the old version.

---

## The Kill Switch
After 5 failed fix attempts on the same bug: abandon the branch.
Save the lessons. Start fresh. You lose the code. You keep the knowledge.

---

## The Self-Improving Loop
End of every chat → V0 updates AI_RULES.md + CONTEXT.md + PROMPT-LOG.md.
Next chat → V0 reads improved files → works better.
The system gets smarter every session. Automatically.

```
Session 1:   Generic rules
Session 10:  Project-specific rules  
Session 30:  Finely tuned rules
Session 50:  The agent knows your codebase better than you do
```

---

*Agile99 -- agile99.com -- github.com/joelfrenette/agile99-starter-kit*
