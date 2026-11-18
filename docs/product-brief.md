# Product Brief: Sports Debrief

Upload a clip of yourself; get back a coach's debrief with one thing to fix.

## Problem
Riders who want to improve already film themselves and ask strangers for help. Reddit replies are free but often sarcastic, contradictory or wrong. Lessons work, but they're expensive and nobody watches every run. General chatbots will comment on a clip, but their advice isn't built around how people learn: too many fixes at once, no priorities, no next step. Nobody gives a rider a structured, coach-quality debrief of their own clip on demand.

## Target user
A beginner-to-intermediate snowboarder who has a friend film them and posts the clip online asking "what am I doing wrong?" They already film and already want feedback; the feedback they get is poor.

## First sport and skill range
- **POC (v0, local):** snowboarding, beginner to intermediate (first turns, linked turns, carving).
- **v1 (public):** snowboarding and skiing, beginner to expert.
- Skiing is the deliberate test that adding a sport is cheap. If adding it blows the budget, the design is wrong.
- Footage must be third-person and show the full body (a friend filming or a selfie stick). Helmet-cam footage is rejected.

## Core loop
1. Rider uploads a clip and answers three questions: *What were you trying to do? How did it feel? What do you think went wrong?* They can add a specific question.
2. The app confirms the sport and checks the footage. Unusable clips come back with filming tips.
3. Rider gets one coaching report:
   1. **What's working:** 2–3 specifics
   2. **One focus:** the root cause, phrased as what to do, plus a short cue phrase
   3. **Where it shows:** timestamps and 1–3 stills with a skeleton overlay, tied to the rider's own answers
   4. **Why it matters:** what this fix unlocks next in the progression
   5. **One drill**, with reps
   6. **How you'll know:** what it feels like when it's right
   7. **Next run:** a goal, and what to film next
   8. Closes on the cue phrase
4. Rider can ask **up to three follow-up questions** while the session is open.
5. Session ends; the video and analysis are deleted.

The coaching method follows the coach debrief in the USPA *Instructional Rating Manual*: the student assesses first, praise comes first, corrections are few and target the cause, the correct action is named rather than the mistake, cues are about feel, and the debrief ends with a goal for next time.

## MVP scope
**In:** knowledge bases for snowboarding and skiing (skill graph, rubrics, common faults, drills), researched by an LLM from expert sources and reviewed by a person · an admin panel to build, review and add sports · auto sport detection with a confirm fallback · footage triage · the report above, with up to three follow-ups · stills with skeleton overlay · deletion at end of session · a public site with sample reports (own and friends' clips, with permission) and invite-coded uploads · a public repo with README, tests and CI.

**Out:** other sports · fully automated sport onboarding with no human review · open chat or more than three follow-ups · accounts, history, progress tracking, re-assessment across clips · a rider-facing skill graph (it stays internal) · fully annotated video playback · mobile app · monetization · open public uploads (later, with a free allowance per IP once the cost per video is known) · any downloaded third-party clip in the repo or demo.

## Success criteria
1. **Beats generic chatbots:** blind comparison on 15–20 clips per sport against ChatGPT and Gemini with a generic prompt, scored against the coaching method. The app wins the majority. Judged by experienced riders or coaches of that sport.
2. **Honest triage:** usable clips get reports; unusable clips are rejected with a reason instead of a guess.
3. **Adding skiing is cheap:** it costs a small fraction of the snowboarding build (target set after the POC).
4. **Cheap to run:** under $20 a month total.
5. **Readable repo:** a reviewer can understand the public repo in five minutes.

## Key assumptions and risks (feasibility test input)
Test set: our own clips and clips from friends and family (with permission), covering beginner snowboarding and beginner skiing, plus third-party clips used locally for testing only and never committed or published.
1. **Pose tracking holds up on amateur phone video:** a distant rider who is small in the frame, shaky footage, snow glare, baggy clothing, spray.
2. **The video adds signal:** analysis-backed reports beat the same LLM working without the analysis. If not, the edge is just a prompt.
3. **Rubric faults are visible** from a single 2D angle.
4. **The coaching method carries over:** judges rate USPA-style debriefs as better coaching.
5. **The LLM-built knowledge base is reviewable:** errors can be caught in reasonable time, even by a reviewer who doesn't ski.
6. **Cost per video**, including up to three follow-ups, fits the $20 a month ceiling at demo volume.

**Risks:** expert-level faults are subtler and may not be readable from phone video · advice could push a beginner onto terrain beyond their ability · copyright on expert source material in a public repo · platform terms for third-party test clips · bystanders and minors in uploads · cost run-up or abuse once public.

## Open questions
**Product:** What's the policy on minors, and how is consent worded for uploaders and bystanders? · Should expert sources be stored, or only summarized and cited? · Safety disclaimer wording · How are invite codes handed out?

**Architecture (not solved here):** pose model for snow sports · processing cost and hosting per clip · knowledge base structure that makes a new sport mostly data, not code · guaranteeing deletion (storage, logs) · whether S3 is needed at all given deletion at end of session · Streamlit for the public site, or for admin only · rate limiting and abuse controls.
