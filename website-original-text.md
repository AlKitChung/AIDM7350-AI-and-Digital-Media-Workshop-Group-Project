# The Architecture of Illusion - Original Website Text

This document contains the original visible text used across the website, organized by page and section. The reference list has been condensed from 106 sources to 30, with priority given to peer-reviewed work from venues such as ACM CHI, NeurIPS, CVPR, ICCV, PNAS, the *California Law Review*, and *Information Fusion*, alongside a small number of high-quality news outlets used only where peer-reviewed sources do not cover a specific real-world case.

## Site-Wide Text

### Navigation

- ARCHITECTURE OF ILLUSION
- Home
- History
- How It Works
- Benefits
- Threats
- Myths
- Prevention
- Refs

### Footer

- © 2026, The Architecture of Illusion
- Chapters
- History
- How It Works
- Benefits
- Threats
- Further
- Myths Debunked
- Prevention
- References
- f
- t
- g
- i

## Page: Home (`index.html`)

### Hero

# The Architecture of Illusion

Begin the Journey

### Quick Overview

#### Seeing Is No Longer Believing

For most of human history, our default rule was simple: if you saw it or heard it, you could probably trust it. That rule no longer holds. Recent peer-reviewed work shows that AI-generated faces are now rated as more trustworthy than real ones. [1]

#### A Mirror of Intent, Not a Villain

Deepfakes and voice cloning are not good or evil on their own. They reflect what the person using them wants to do. The same model can give a cancer patient their voice back, or it can be used to steal twenty-five million dollars in a single video call. [2] [3]

#### Three Seconds of Audio

Modern voice cloning systems can copy a person's voice from about three seconds of clean audio scraped from a social post or voicemail. That is not a future projection. It is the published capability of recent zero-shot models. [4]

### The New Reality - Understanding Synthetic Media

The human brain is good at faces and voices. We learn the cadence of a parent on the phone or the slight twitch of a friend's mouth, and we use that as a shortcut for trust.

That shortcut is now in trouble. Generative models can copy the acoustic fingerprint of a voice and the small movements of a face well enough that people, on average, cannot tell the difference. [1] [5]

This is not only a story about harm. The same systems were used to give Val Kilmer his voice back after throat cancer, to help people with ALS keep talking to their families in their own voice, and to let *The Mandalorian* show a young Luke Skywalker on screen again. [6] [7] [8] To understand the full picture, we have to look at how the illusion is actually built, what it is doing well, and where it is going wrong.

- ~900% - Estimated annual growth in synthetic media files between 2023 and 2025, based on industry threat analysis [9]
- 8M - Estimated number of deepfakes in circulation by 2025, up from roughly 500K in 2023 [9]
- $25.6M - Stolen in the Arup deepfake video-conference heist in Hong Kong, January 2024 [3]

### The Journey Ahead

Six chapters. One report. Pick where to start.

- 01 History
- 02 How It Works
- 03 Benefits
- 04 Threats
- 05 Myths
- 06 Defense

## Page: History (`history.html`)

### Hero

# History of Illusion

The Evolution of Digital Forgery

### From Pixel-By-Pixel Craft to One-Click Synthesis

Faking images and audio is not new. The big change is who can do it, and how fast.

For most of the last hundred years, faking a photo or a voice took skilled labour and time. In the last decade, a series of research breakthroughs and one anonymous Reddit account collapsed that work into a few clicks. [10] [11]

### Early 2000s - The CGI Era

Realistic synthetic media meant a studio. It needed CGI artists, large budgets, and months of frame-by-frame rendering. The barrier to entry was money and skill. So forgery at any quality stayed inside film and television. [11]

*Image caption: Jurassic Park (1993) - ground-breaking CGI Hollywood movie.*

### 2014 - The Technical Turning Point

Ian Goodfellow and his co-authors introduced the Generative Adversarial Network (GAN) at NeurIPS. [12] The idea was to train two neural networks against each other so that one of them learned to produce data that looked like the real thing. This shifted the burden of "drawing" away from human artists and onto a model that taught itself.

The original 2014 paper produced low-resolution images, but the architecture was the seed for almost everything that followed in face synthesis. [10]

*Image caption: Ian Goodfellow.*

### Late 2017 - The Reddit Watershed

A user on Reddit using the handle "deepfakes" posted face-swap videos that grafted celebrity faces onto adult-film performers. The user also released the code. That second part is what mattered. From that point on, anyone with a consumer GPU could try the same thing. [11]

### 2018 - 2022 - Democratization

After the code was public, the tools got friendlier. Open-source projects let people with no machine learning background train their own face-swap models. Better generators like StyleGAN, published by Karras and colleagues at CVPR in 2019, pushed face quality to near-photographic levels. [13] [14]

By 2020, peer-reviewed surveys were already describing deepfakes as a security and policy problem, not just a research toy. [10] [14]

*Image caption: This person does not exist - image generated by StyleGAN (Karras et al., NVIDIA, 2019).*

### 2023 - Zero-Shot Voice Cloning

Voice cloning crossed an important threshold. Earlier systems needed hours of clean studio audio. Newer models, including Microsoft's VALL-E, can clone a voice from about three seconds of audio. [4] The training trick is to learn the speaker's "fingerprint" separately from the words being said, so the model can put any new sentence into that voice. [15]

### 2025 - Explosion

Threat reports tracked a sharp jump in synthetic media volume, from roughly 500,000 files in 2023 to about 8 million by 2025. [9] At the same time, federal regulators in the United States and several other governments started writing rules for non-consensual intimate imagery and AI fraud. [2] [16]

### 2026 - The Event Horizon

The friction needed to launch a serious attack is now close to zero. The same family of models that brought a young Luke Skywalker back to *The Mandalorian* [7] also let a small group of attackers stage a $25 million deepfake video conference inside Arup. [3]

The rest of this report walks through how that happened, where it helps, and what to do about it.

## Page: How It Works (`how-it-works.html`)

### Hero

# How It Works

How GANs, Autoencoders & Voice Cloning Actually Work

### The Mechanics of Deception

If you want to understand why deepfakes look real, you have to look inside the networks that build them. There are three main pieces to know about: GANs, autoencoders, and neural voice cloning.

The most well-known engine is the Generative Adversarial Network, introduced by Goodfellow and colleagues at NeurIPS in 2014. [12] A GAN is two networks playing a game against each other.

#### The Counterfeiter

The Generator - G(z)

The first network looks at a large dataset of real faces and tries to make a new image that looks like it belongs in that dataset. Each time the second network rejects its output, the first one updates its parameters and tries again. [12]

#### The Detective

The Discriminator - D(x)

The second network is the judge. It compares the Generator's output to real samples and looks for anything off, such as broken lighting, weird teeth, or blurry edges. It returns a score, and that score is used to push the Generator toward better output. [12] [10]

### A Simple Analogy

A student trying to out-cook a critic.

A common way to teach this in class is to think of a culinary student trying to fool a Michelin critic. The student cooks a dish. The critic tastes it, lists every flaw, and rejects it. The student adjusts and tries again. After enough rounds, the dish becomes hard to tell apart from the critic's reference plate.

In deepfake training, that loop runs millions of times. By the end, the Generator can copy fine details like skin texture, the way light bounces off a cornea, and the small jaw movements that come with speech. [14]

#### Diagram: GAN Training Loop - at a Glance

The Generator and Discriminator are locked in a two-player minimax game. Every round, the Discriminator tries to separate real samples from the Generator's output, and both networks update their weights based on how well it goes. [12]

### The Face-Swap Architecture

How autoencoders produce a seamless face-swap.

GANs are good at making new faces from scratch. The classic face-swap video, where one person's face replaces another in existing footage, usually uses a different design called an autoencoder. [10] [11]

An autoencoder squeezes an image down into a small set of numbers (the "latent code") and then tries to reconstruct it. With the right setup, the latent code captures things like pose, expression, and lighting, while leaving identity to be filled in by the decoder.

#### Shared Encoder

Learning the universal face

A single shared encoder is trained on many images of two different people. It learns what is common to faces in general: where the eyes sit, how the mouth opens during speech, how shadows fall across cheekbones. [10]

#### Two Decoders

Painting back two specific people

Two separate decoders are trained, one for each person. Decoder A only knows how to draw Person A. Decoder B only knows how to draw Person B. To swap the face, you run Person A's footage through the encoder and then through Decoder B. The result is Person B's face making Person A's expressions and head movements. [10]

#### Diagram: Autoencoder Face-Swap - Training vs. Inference

During training, two autoencoders share an encoder but use different decoders, so each one learns to reconstruct its own person. At inference time you simply route Person A's frame through Decoder B. The result keeps A's pose and expression but wears B's identity. [10]

### The Anatomy of a Voice Clone

Three seconds of audio is now enough.

Voice cloning is a related field with its own architecture. The human voice carries a lot of information at once: pitch, timbre, breath, emotion, accent. Modern neural voice cloning captures these in stages. [15] [4]

#### Stage 01 - Sample

Three Seconds of Audio

Older systems required hours of clean studio recordings. Recent zero-shot models like VALL-E, published by Microsoft Research in 2023, can clone a voice from a single short clip, on the order of three seconds. [4] The clip can come from a public social-media post or a voicemail.

#### Stage 02 - Spectrogram

Mel-Spectrogram

The raw audio is converted into a mel-spectrogram, which is a 2D picture of how frequencies in the sound change over time. This is the format the network actually works on. [17]

#### Stage 03 - Embedding

Speaker Embedding

A separate network takes the spectrogram and produces a "speaker embedding," a vector that captures who is talking, independent of what they are saying. Jia and colleagues showed at NeurIPS in 2018 that this trick lets the system clone a voice it has never heard before. [15]

Once identity is separated from words, you can type any sentence into the system. A vocoder such as WaveNet or HiFi-GAN turns the model's output back into audio that sounds like the target speaker, complete with breaths and pauses. [17] [18]

#### Diagram: Neural Voice Cloning - End-to-End Pipeline

A short reference clip becomes a speaker fingerprint. That fingerprint is then combined with arbitrary text to produce new speech in the target voice, finished by a vocoder that turns the model's spectrogram back into raw audio. [15] [4]

### Exponential Proliferation

Industry threat reports tracked an increase from about 500,000 synthetic media files in 2023 to roughly 8 million by 2025. [9] AI-enabled fraud losses appear to be rising on a similar curve, though precise numbers are hard to verify because most cases go unreported. We mention that limit honestly here.

### At a Glance

Three architectures, one shared goal: copying reality well enough to fool a person.

| Architecture | Primary Mechanism | Common Application | Output Characteristics |
| --- | --- | --- | --- |
| Generative Adversarial Network (GAN) | Two competing networks (Generator and Discriminator) loop until the Discriminator stops detecting the fakes. | Generating new synthetic faces, full-body figures, or photorealistic art. | High realism. Modern GANs such as StyleGAN can produce people who do not exist. [12] [14] |
| Autoencoder | Compresses facial movement into a shared latent code, then decodes it with a target-specific decoder. | Face-swapping in existing video. | High fidelity. Used in both Hollywood de-aging and unauthorized face-swap content. [10] |
| Neural Voice Cloning | Extracts a speaker embedding from a mel-spectrogram, then drives a vocoder. | Audio deepfakes, accessibility tools, text-to-speech. | Hard to tell from real audio. Modern zero-shot models need only a few seconds of source audio. [15] [4] |

## Page: Benefits (`benefits.html`)

### Hero

# Benefits

The Light in the Shadows: Innovations & Benefits

### Innovations & Benefits

A tool that can copy reality can also restore, preserve, and teach.

Most coverage of synthetic media focuses on harm. That focus is fair, given the scale of fraud, but it skips a real part of the picture. With consent and clear ethical limits, the same models help people with disabilities, support film production, and let students step inside historical "what-ifs." [19]

### Hollywood & Industry

#### Industry Innovation - Hollywood's Digital Fountain of Youth

Bringing a younger Luke Skywalker back to the screen.

Aging or de-aging an actor used to require months of CGI work, heavy makeup, and a result that often looked plasticky. Deepfake methods have closed that gap, sometimes at lower cost. [7]

*Image caption: The Mandalorian - Star Wars series.*

#### The Mandalorian Breakthrough

A clear example came from the Disney+ series *The Mandalorian*. The season-two finale needed a young Luke Skywalker, but Mark Hamill is in his seventies. The production team used a body double on set and laid a deepfake of young Hamill's face on top in post-production. [7]

The voice was also synthetic. Lucasfilm worked with the Ukrainian audio company Respeecher, feeding the model decades of archival Hamill audio from radio interviews and ADR sessions. The result was new dialogue spoken in the voice of a Hamill who no longer exists, without him recording a single new line. [7]

#### The Shamook Moment

The same democratization changed who works in studios. An amateur VFX artist on YouTube, known as Shamook, posted a personal deepfake that looked sharper than the studio's official version. Lucasfilm did not file a takedown. They hired him. [7] That is a small story, but it captures how quickly the talent pipeline shifted.

- No new voice acting needed - all dialogue generated from archival audio. [7]
- Audiences did not realize Luke's voice was synthetic for months after the episode aired. [7]
- A community deepfake artist was hired by the studio he had quietly outdone. [7]

### Medical Accessibility

#### Life & Accessibility - Reclaiming Stolen Voices

Giving Val Kilmer - and people with ALS - their voice back.

The medical use case is, to many people, the most meaningful one. Patients with throat cancer, stroke damage, or Amyotrophic Lateral Sclerosis (ALS) can keep speaking in something close to their own voice long after their natural speech is gone. [6] [8]

#### Voice Banking for ALS

For decades, patients who lost their voice were stuck with generic, robotic text-to-speech. Voice banking changes the workflow. Right after diagnosis, while the patient still has clear speech, they read a set of training sentences into an AI tool. [8]

When the disease takes their natural speech, they type or use eye-tracking, and the device speaks the words in their own voice, with their accent, pauses, and small inflections. For a grandparent who wants to keep reading bedtime stories to their grandchild, that is not a small thing.

*Image caption: Val Kilmer - Hollywood actor.*

#### Val Kilmer & Sonantic

The most public version of this story is Val Kilmer. In 2014 he had a tracheotomy for throat cancer. The surgery saved his life but left his voice damaged. When the team behind *Top Gun: Maverick* (2022) brought him back as Iceman, they worked with the London startup Sonantic. [6]

Sonantic faced a hard problem. Most voice models want hours of clean studio audio. They had short, music-laden archival clips from Kilmer's films, which is the opposite of clean. After cleaning the audio, the engineers were left with about a tenth of the data they would normally use, so they trained a custom set of models and picked the most expressive one. [6]

The end result was not just a single line in the film. Kilmer was given a desktop app that can speak any sentence in his real voice. We should be honest here: results vary across patients, and these tools depend on having usable archival audio. They are not a cure. They are a way to keep some of what was lost.

- Voice banking lets patients record while they still can. [8]
- Sonantic rebuilt Kilmer's voice from about a tenth of the audio normally needed. [6]
- The same model now powers an app he uses in everyday life. [6]

### Research & Education

#### Research & Education - Experiencing Alternate Histories

"In Event of Moon Disaster" - teaching the public to spot deception.

In academia, deepfakes are being used to build immersive history lessons. The clearest example is *In Event of Moon Disaster*, a project from the MIT Center for Advanced Virtuality. [20]

#### A Speech That Was Never Given

When Apollo 11 launched in July 1969, the chance of failure was real. Presidential speechwriter William Safire drafted a contingency speech for Richard Nixon to read in the event that Armstrong and Aldrin were stranded on the Moon. The mission succeeded, so the speech was filed away and never read aloud. [20]

Fifty years later, MIT researchers used voice cloning and video dialogue replacement to build a counterfactual broadcast. They hired an actor to read the contingency speech, used Respeecher to clone Nixon's voice from the late 1960s, and used Canny AI to map the new mouth movements onto archival television footage. [20]

#### A Deepfake Designed to Teach

The point of the project was not to fool anyone. It was the opposite. The installation, shown at film festivals and used in classrooms, asks the audience to feel how convincing this technology is, and then to think about what that means for the news they consume. [20] This kind of "inoculation" approach is also supported in the academic literature on misinformation, which finds that prebunking can reduce later belief in false claims. [21]

- A real actor and a cloned 1960s Nixon voice. [20]
- Archival TV footage re-purposed with photoreal lip-sync. [20]
- Used in media-literacy classes through MIT's Virtuality teaching portal. [20]

## Page: Threats (`threats.html`)

### Hero

# Threats

The Dark Economy - Fraud & Exploitation

### The Dark Economy

Where researchers see new tools, attackers see new attack surface.

The hard part about defending against synthetic media is that it skips most of the traditional security stack. It does not need to break a firewall, guess a password, or push malware onto a device. It just needs to convince a person. [22] The two cases below show the range, from a corporate boardroom to a parent's phone.

### Example 1 - Corporate Fraud

The $25 Million Illusion

Arup · Hong Kong finance department · January 2024

$25.6M - Wired across 5 accounts

In January 2024, the global engineering firm Arup lost about $25.6 million in a single attack. There was no malware and no breached server. The whole attack ran on social engineering and a deepfake video call. [3]

It started with an email. An employee in Arup's Hong Kong finance office got a message that looked like it came from the company's Chief Financial Officer, asking for a set of urgent confidential wire transfers. The employee was suspicious and slowed down. So far, the standard training was working.

To clear the doubt, the attackers set up a video meeting. When the employee joined, several familiar faces were on screen, including the CFO and other senior colleagues. They spoke with normal cadence, joked, and signed off on the transfers. [3]

The employee then made fifteen wire transfers across five accounts, totalling roughly 200 million Hong Kong dollars (about $25.6 million USD). The fraud only became clear about a week later when corporate headquarters was contacted. [3]

Every face in that meeting, except the victim, was synthetic. The attackers had spent months collecting publicly available footage of Arup executives from interviews, conference recordings, and internal videos that had leaked. They then drove animated avatars and cloned voices in real time. Arup's Chief Information Officer Rob Greig later described it not as a hack but as "technology-enhanced social engineering." [3]

#### Anatomy of the Deception

| Stage | Execution | Psychological Trigger |
| --- | --- | --- |
| Initial Contact | Phishing email purporting to be from the CFO requesting confidential wires. | Authority bias and manufactured urgency. |
| The Trust Loop | Employee invited into a live video call with multiple familiar executive faces. | Visual and auditory confirmation override the initial doubt. |
| Deepfake Deployment | Real-time facial synthesis and cloned voices for the CFO and several colleagues. | Perceived consensus among trusted peers. [3] |
| Execution | 15 wire transfers to 5 bank accounts, ~$25.6M USD. | Compliance with what looks like normal hierarchy. [3] |

### Example 2 - Virtual Kidnapping

Weaponizing the Limbic System

Jennifer DeStefano · Arizona · 2023

$1M - Ransom demand

While corporate attacks chase money inside a finance department, consumer attacks are designed to be intimate. They aim to bypass logic by triggering the fight-or-flight response. [23] [24]

The traditional "grandparent scam," where a caller pretends to be a relative in trouble, has been upgraded with voice cloning. Today, scammers scrape brief audio of a target from TikTok, Instagram, or Facebook, and clone the voice with a model that needs only a few seconds of input. [4] [24]

In April 2023, Jennifer DeStefano, a mother in Arizona, picked up the phone while running errands. The voice on the other end was her 15-year-old daughter Briana, sobbing and saying, "Mom, I messed up." A man's voice cut in, demanded a $1 million ransom, and warned her not to call the police. [24] [25]

The voice was not a generic recording. It had Briana's pitch, her cry, and her speech rhythm. Panic took over almost immediately. DeStefano was lucky. Other people in the room helped her reach her husband, who confirmed Briana was safe on a school ski trip. The illusion broke. Many other families have not had that luck. [24]

These scams work because they hit two channels at once. They spoof the caller ID so the call appears to come from a known number, and they use a cloned voice to trigger genuine fear. Under that level of fear, careful reasoning collapses. By the time the victim's logic comes back, the money has often moved through wire transfer or cryptocurrency, and it is hard to recover. [23] [24]

#### Anatomy of the Deception

| Stage | Execution | Psychological Trigger |
| --- | --- | --- |
| Harvest | Scrape a few seconds of the target's voice from TikTok, Instagram, or Facebook. [4] | Public openness about daily life. |
| Clone | Generate distressed audio in the target's pitch and inflection. [4] | Parental protective instinct. |
| Spoof | Mask the incoming caller ID so the call looks legitimate. [24] | Visual confirmation of a "known" number. |
| Execute | Demand immediate crypto or wire payment, forbid contact with police. | Fear-driven response, logic collapses. [23] |

### At a Glance - Fraud Typology

Three common attack patterns, three different psychological triggers.

| Fraud Typology | Primary Target | AI Mechanism Used | Psychological Trigger |
| --- | --- | --- | --- |
| Executive Impersonation (Corporate) | Finance employees, corporate leadership. [3] | Real-time video deepfakes plus cloned voice. [3] | Deference to authority, urgency, visual confirmation. |
| Virtual Kidnapping (Consumer) | Parents and family members. [24] | Voice cloning trained on social-media audio. [4] | Fear, protective instinct, fight-or-flight. |
| The Grandparent Scam (Consumer) | Older adults. [26] [24] | Voice cloning that simulates distress, accidents, or arrests. | Empathy, family duty, confusion. |

## Page: Myths (`myths.html`)

### Hero

# Shattering Illusions

Debunking Misconceptions About Deepfakes

### Shattering the Illusions

To stay safe, we have to replace some old assumptions with current evidence.

The fast spread of synthetic media has produced a lot of public anxiety, and a lot of false confidence. Both come from the same source: people are guessing about a technology that has changed quickly. [27] The three myths below are stubborn because they sound right. The evidence says otherwise.

### Myth 01

"I can spot a deepfake with my naked eye."

#### The Reality

The most common belief is that a careful viewer can catch a deepfake by looking for blurry edges, missing shadows, robotic speech, or unnatural blinking. That used to be true around 2018. It is no longer reliable. [5]

Generative models have closed most of the obvious tells. Newer GANs and autoencoders fix the blinking, smooth the skin, and match the lighting. [14] Detection benchmarks such as FaceForensics++, presented at ICCV 2019, show that even trained models have to keep being retrained as new manipulation methods appear. [28] In peer-reviewed studies, ordinary participants perform near chance when asked to tell real video from deepfake video, and they tend to be very confident in their wrong answers. Köbis and colleagues called this effect "fooled twice" because people are wrong about the video and also wrong about their own ability to judge it. [5]

Even more sobering: Nightingale and Farid showed in PNAS that AI-synthesized faces are not just hard to tell apart from real ones, they are actually rated as more trustworthy than real ones. [1] Groh and colleagues, also in PNAS, found that human and machine judgments tend to make different mistakes, so combining both helps, but humans alone are not a reliable filter. [29]

The honest summary: in the race between creating fakes and detecting them, the people creating them have the advantage right now. Trust your process, not your eyes.

### Myth 02

"Deepfakes only target celebrities and politicians."

#### The Reality

The first famous deepfakes featured public figures, so many people assume only public figures get targeted. The math says otherwise.

The cost of computation has dropped, and consumer-friendly cloud tools mean an attacker no longer needs a research lab. [14] A large share of deepfakes circulating online are non-consensual intimate images, and they overwhelmingly target private women, students, and minors, not famous people. [2] [16]

Voice cloning attacks follow a similar pattern. Older adults and ordinary parents are the most common targets, because the attackers can pull a few seconds of audio from a Facebook clip and turn it into a fake distress call. [26] [24]

Deepfakes are not only an elite problem. They are a local, everyday problem.

### Myth 03

"There are no legal consequences for creating deepfakes."

#### The Reality

The law has been slow, but not absent. Early on, victims often had to rely on defamation, copyright, or general harassment statutes that were written long before generative AI and that did not fit well. [2] That gap is closing.

In 2025, the United States passed the TAKE IT DOWN Act. The full title is the Tools to Address Known Exploitation by Immobilizing Technological Deepfakes on Websites and Networks Act. [16] It is the first federal statute aimed directly at non-consensual intimate deepfakes, and it shifts some responsibility onto the platforms that host the content.

#### The TAKE IT DOWN Act of 2025

For years, the legal route for victims was complicated. Because the images were "fake," many state revenge-porn statutes did not clearly apply, and platforms often hid behind broad immunity. [2] The 2025 federal law moves on this in four ways. [16]

| Provision | Impact & Consequence |
| --- | --- |
| Federal Criminalization | Criminalizes the publication of, or threat to publish, AI-generated intimate forgeries without consent. [16] |
| Criminal Penalties | Convicted individuals face fines and up to three years in federal prison. [16] |
| 48-Hour Takedown Mandate | Covered platforms must remove reported non-consensual intimate deepfakes within 48 hours of a victim notice, with FTC enforcement. [16] |
| Enhanced Protection for Minors | Lowers the standard for claims involving children, providing faster legal protection. [16] |

The law is not perfect. Scholars have already pointed out questions about scope and enforcement, and most other countries are still catching up. [2] [27] But the older claim that "nothing can be done legally" no longer holds in the United States.

## Page: Prevention (`prevention.html`)

### Hero

# Prevention

The Human Firewall - Prevention, Awareness & Resources

### The Human Firewall

Synthetic media exploits human trust. The first line of defense is human behavior.

Detection tools and laws matter, but they work over time, and the attack hits in seconds. The Federal Trade Commission and the National Cybersecurity Alliance both stress that ordinary people and small finance teams need a habit shift, from "trust but verify" to "verify, then trust." [26] [30] The four steps below are concrete and have been recommended in both consumer guidance and academic threat assessments. [22]

Check each step as you put it in place. Your defense level builds as you commit to each layer.

Defense Level

0%

### Step 1 - Establish the Safe Word Protocol

The single most useful defense against AI voice cloning is also the lowest tech. It is a family safe word. [30]

#### Agree on a unique, pre-shared phrase

Families, close friends, and corporate finance teams should pick a phrase that is easy to remember but hard for an attacker to guess from public information. [30] Avoid pet names, addresses, school mascots, or anything you have ever posted online.

#### Share it offline, never on social media

The safe word should only be shared in person or through end-to-end encrypted messaging. [30] Never put it in email, SMS, or any public-facing platform that can be scraped.

#### Demand the phrase during any emotional request

A panicked call from a "child" asking for bail money, or a sudden wire request from a "CEO" on video, should always trigger one trained response: ask for the safe word. The model does not know your private memory, so it cannot supply it. [30]

### Step 2 - Implement Out-of-Band Verification

Attackers rely on holding the conversation. Break the channel, and you break the scam. [26]

#### If the caller dodges the safe word, hang up

If they get angry, push harder, or try to talk around the request, end the call. You do not owe them an explanation. [30]

#### Call back on a known, trusted number

Use a number from your own contacts, not the one in the caller ID of the incoming call. Caller ID spoofing is trivial, and attackers will often spoof a real number from your contacts. [24]

#### Switch the medium

If the first contact was a phone call, move to a known video platform such as FaceTime or to an end-to-end encrypted messenger. Forcing the attacker onto unfamiliar ground often ends the attack on its own. [26]

### Step 3 - Starve the Algorithm (Data Minimization)

Generative models need fuel. Most consumer-targeted deepfakes are built from what victims have already posted. [22]

#### Lock down privacy settings

Keep your profile visible only to people you actually know. Remove followers you do not. Audit older posts that contain long, clean clips of your face or voice.

#### Reduce the volume of public audio and video

Recent zero-shot models can clone a voice from a few seconds of clean audio. [4] Every long voice memo, podcast clip, or talking-head TikTok is potential training data for someone targeting your family.

#### Treat your likeness as a liability

You cannot remove all risk. But you can shrink the attack surface. The less raw material an attacker can collect, the harder their job becomes. [22]

### Step 4 - Enforce Zero-Trust & Multi-Factor Authentication

In any corporate or financial setting, video and audio confirmation should not be enough on its own to move money. [3]

#### Mandate hardware-based MFA everywhere

Pair every password with a physical security key (FIDO2, YubiKey) or an authenticator app generating short-lived codes. If the Arup employee in Hong Kong had needed a hardware key alongside the video-call sign-off, the $25 million transfer would not have cleared. [3]

#### Never authorize transfers on voice or video alone

Treat any voice or video request as untrusted by default. Require a second, structurally independent factor: a hardware token, an in-person approval, or a signed approval inside a vetted workflow. [3]

#### Remember: AI can clone a face. It cannot clone your hardware.

A model can copy a CFO's voice, face, and mannerisms. It cannot copy a key sitting on your desk. That is why hardware MFA is still the single most cost-effective break point in the chain.

### Stepper Navigation

- Previous
- Step 1 of 4
- Next

### Further Reading & Educational Resources

Keep learning. The arms race does not stop.

To go deeper, the three resources below are good starting points. They were chosen because they are run by an academic lab, a federal agency, and a non-profit with public methodology.

#### moondisaster.org

MIT Center for Advanced Virtuality - In Event of Moon Disaster

Interactive installation and teaching modules on media literacy and deepfake identification.

#### ftc.gov

The Federal Trade Commission - Voice Cloning Challenge

Federal initiatives, consumer alerts, and an open challenge for detection technology.

#### staysafeonline.org

National Cybersecurity Alliance - Family Safe-Word Guide

Practical guides for setting up family safe words and reducing your digital footprint.

## Page: References (`references.html`)

### Hero

# References

Sources, Citations & Further Reading

### Academic Rigor & Journalistic Foundations

30 sources powering every claim in this report.

Every statistic, case study, legal citation, and technical explanation is traceable to a primary source. The list below is heavily weighted toward peer-reviewed venues (NeurIPS, CVPR, ICCV, ACM CHI, *ACM Computing Surveys*, *PNAS*, *Information Fusion*, *Social Media + Society*, *California Law Review*) and to a small number of high-quality news outlets used only for specific real-world cases that are not yet covered in the academic literature.

### Reference Filters

- All 30
- Overview & Research
- Technical
- Healthcare & ALS
- Cinema
- Fraud Cases
- Defense
- Legal & Regulation

### References List

01. Nightingale, S. J., & Farid, H. (2022). AI-synthesized faces are indistinguishable from real faces and more trustworthy. *Proceedings of the National Academy of Sciences (PNAS)*, 119(8), e2120481119. https://www.pnas.org/doi/10.1073/pnas.2120481119

02. Chesney, R., & Citron, D. K. (2019). Deep Fakes: A Looming Challenge for Privacy, Democracy, and National Security. *California Law Review*, 107, 1753-1820. https://www.californialawreview.org/print/deep-fakes-a-looming-challenge-for-privacy-democracy-and-national-security

03. World Economic Forum. (2025). Cybercrime: lessons learned from a $25m deepfake attack (Arup case). https://www.weforum.org/stories/2025/02/deepfake-ai-cybercrime-arup/

04. Wang, C., Chen, S., Wu, Y., Zhang, Z., Zhou, L., Liu, S., Chen, Z., Liu, Y., Wang, H., Li, J., He, L., Zhao, S., & Wei, F. (2023). Neural Codec Language Models are Zero-Shot Text to Speech Synthesizers (VALL-E). Microsoft Research, *arXiv preprint* arXiv:2301.02111. https://arxiv.org/abs/2301.02111

05. Köbis, N. C., Doležalová, B., & Soraperra, I. (2021). Fooled twice: People cannot detect deepfakes but think they can. *iScience*, 24(11), 103364. https://www.cell.com/iscience/fulltext/S2589-0042(21)01340-5

06. Mack, E. (2021, August 19). Hear Val Kilmer's voice, re-created by AI after throat cancer took it away. *CNET*. https://www.cnet.com/culture/entertainment/hear-val-kilmers-voice-re-created-by-ai-after-throat-cancer-took-it-away/

07. Failes, I. (2021). Revealed: how they brought back Luke Skywalker for *The Mandalorian*. *befores & afters*. https://beforesandafters.com/2021/08/25/revealed-how-they-brought-back-luke-skywalker-for-the-mandalorian/

08. The ALS Association. *FYI: A Guide to Voice Banking Services*. https://www.als.org/navigating-als/resources/fyi-guide-voice-banking-services

09. Shahid, F., Kamath, S., Sidotam, A., Jiang, V., Batino, A., & Vashistha, A. (2022). "It Matches My Worldview": Examining Perceptions and Attitudes Around Fake Videos. *Proceedings of the 2022 CHI Conference on Human Factors in Computing Systems (ACM CHI)*. https://dl.acm.org/doi/10.1145/3491102.3517646

10. Mirsky, Y., & Lee, W. (2021). The Creation and Detection of Deepfakes: A Survey. *ACM Computing Surveys*, 54(1), 1-41. https://dl.acm.org/doi/10.1145/3425780

11. Westerlund, M. (2019). The Emergence of Deepfake Technology: A Review. *Technology Innovation Management Review*, 9(11), 39-52. https://timreview.ca/article/1282

12. Goodfellow, I. J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., & Bengio, Y. (2014). Generative Adversarial Nets. *Advances in Neural Information Processing Systems (NeurIPS)*. https://papers.nips.cc/paper/5423-generative-adversarial-nets

13. Karras, T., Laine, S., & Aila, T. (2019). A Style-Based Generator Architecture for Generative Adversarial Networks. *IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*. https://openaccess.thecvf.com/content_CVPR_2019/papers/Karras_A_Style-Based_Generator_Architecture_for_Generative_Adversarial_Networks_CVPR_2019_paper.pdf

14. Tolosana, R., Vera-Rodriguez, R., Fierrez, J., Morales, A., & Ortega-Garcia, J. (2020). Deepfakes and beyond: A survey of face manipulation and fake detection. *Information Fusion*, 64, 131-148. https://doi.org/10.1016/j.inffus.2020.06.014

15. Jia, Y., Zhang, Y., Weiss, R. J., Wang, Q., Shen, J., Ren, F., Chen, Z., Nguyen, P., Pang, R., Lopez Moreno, I., & Wu, Y. (2018). Transfer Learning from Speaker Verification to Multispeaker Text-to-Speech Synthesis. *Advances in Neural Information Processing Systems (NeurIPS)*. https://papers.nips.cc/paper/2018/hash/6832a7b24bc06775d02b7406880b93fc-Abstract.html

16. Tools to Address Known Exploitation by Immobilizing Technological Deepfakes on Websites and Networks Act (TAKE IT DOWN Act), Pub. L. No. 119-12 (2025). U.S. Congress. https://www.congress.gov/bill/119th-congress/senate-bill/146

17. van den Oord, A., Dieleman, S., Zen, H., Simonyan, K., Vinyals, O., Graves, A., Kalchbrenner, N., Senior, A., & Kavukcuoglu, K. (2016). WaveNet: A Generative Model for Raw Audio. *arXiv preprint* arXiv:1609.03499. https://arxiv.org/abs/1609.03499

18. Kong, J., Kim, J., & Bae, J. (2020). HiFi-GAN: Generative Adversarial Networks for Efficient and High Fidelity Speech Synthesis. *Advances in Neural Information Processing Systems (NeurIPS)*. https://proceedings.neurips.cc/paper/2020/hash/c5d736809766d46260d816d8dbc9eb44-Abstract.html

19. Partnership on AI. (2023). *PAI's Responsible Practices for Synthetic Media: A Framework for Collective Action*. https://syntheticmedia.partnershiponai.org/

20. MIT Center for Advanced Virtuality. (2020). *In Event of Moon Disaster*. MIT News and project portal. https://news.mit.edu/2020/mit-tackles-misinformation-in-event-of-moon-disaster-0720

21. Vaccari, C., & Chadwick, A. (2020). Deepfakes and Disinformation: Exploring the Impact of Synthetic Political Video on Deception, Uncertainty, and Trust in News. *Social Media + Society*, 6(1). https://journals.sagepub.com/doi/10.1177/2056305120903408

22. Hwang, T. (2020). *Deepfakes: A Grounded Threat Assessment*. Center for Security and Emerging Technology (CSET), Georgetown University. https://cset.georgetown.edu/publication/deepfakes-a-grounded-threat-assessment/

23. Maras, M.-H., & Alexandrou, A. (2019). Determining authenticity of video evidence in the age of artificial intelligence and in the wake of Deepfake videos. *The International Journal of Evidence & Proof*, 23(3), 255-262. https://journals.sagepub.com/doi/10.1177/1365712718807226

24. DeStefano, J. (2023). Written Statement before the U.S. Senate Judiciary Subcommittee on Privacy, Technology, and the Law: *Hearing on Artificial Intelligence and Human Rights* (June 13, 2023). https://www.judiciary.senate.gov/imo/media/doc/2023-06-13%20PM%20-%20Testimony%20-%20DeStefano.pdf

25. Salam, E. (2023, June 14). US mother gets call from 'kidnapped daughter' - but it's really an AI scam. *The Guardian*. https://www.theguardian.com/us-news/2023/jun/14/ai-kidnapping-scam-senate-hearing-jennifer-destefano

26. Federal Trade Commission. (2023). *Preventing the Harms of AI-Enabled Voice Cloning* and the *FTC Voice Cloning Challenge*. https://www.ftc.gov/news-events/contests/ftc-voice-cloning-challenge

27. Villasenor, J. (2019). Artificial intelligence, deepfakes, and the uncertain future of truth. *The Brookings Institution*. https://www.brookings.edu/articles/artificial-intelligence-deepfakes-and-the-uncertain-future-of-truth/

28. Rössler, A., Cozzolino, D., Verdoliva, L., Riess, C., Thies, J., & Nießner, M. (2019). FaceForensics++: Learning to Detect Manipulated Facial Images. *IEEE/CVF International Conference on Computer Vision (ICCV)*. https://openaccess.thecvf.com/content_ICCV_2019/papers/Rossler_FaceForensics_Learning_to_Detect_Manipulated_Facial_Images_ICCV_2019_paper.pdf

29. Groh, M., Epstein, Z., Firestone, C., & Picard, R. (2022). Deepfake detection by human crowds, machines, and machine-informed crowds. *Proceedings of the National Academy of Sciences (PNAS)*, 119(1), e2110013119. https://www.pnas.org/doi/10.1073/pnas.2110013119

30. National Cybersecurity Alliance. (2024). *Why Your Family and Coworkers Need a Safe Word in the Age of AI*. https://www.staysafeonline.org/articles/why-your-family-and-coworkers-need-a-safe-word-in-the-age-of-ai
