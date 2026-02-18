# CausalTrack: Audio-Based Behavioral Truth Detection

**A personal research project exploring multimodal AI for detecting the Say-Do Gap in user research.**

> 🎓 Part of my Computational Product Research learning journey  
> 📅 February 2026  
> 🔬 Methodology validation study 

---

## The Problem

Research shows that **42% of startup failures** are attributed to misreading market demand - building products users said they wanted during research, but refused to adopt upon launch.

One of the potential culprits? **Social Desirability Bias** - users smooth over negative feedback to be polite.

Someone might say: *"This feature is easy to use."*

But their audio reveals: *"It's... [pause 3s]... easy."* [frustrated tone]

**Traditional text-based research misses this gap entirely.**

---

## The Hypothesis

Can we automatically detect the Say-Do Gap by analyzing **audio behavioral cues** using multimodal AI?

- Pauses (>2 seconds)
- Vocal hesitation ("um", "uh")
- Frustrated tone
- Confused tone
- Sentiment mismatch

---

## The Experiment

**Dataset:** 50 synthetic user interviews (AcmeCal - a fictional camping gear rental marketplace)

**Bias Injection:**
- 40 Admin users (smooth experience)
- 10 End Users (friction-filled experience)

**Analysis Pipeline:**
1. Text → Audio (OpenAI TTS)
2. Audio → Behavioral Cues (Gemini 3 Pro)
3. Cues → Knowledge Graph (Neo4j)
4. Graph → Say-Do Consistency Score

---

## The Results

**Say-Do Consistency Scores:**

| User Segment | Score | Interpretation |
|--------------|-------|----------------|
| **Admin Users** | **83.0%** | HIGH CONSISTENCY - Trustworthy feedback ✅ |
| **End Users** | **3.2%** | LOW CONSISTENCY - Hidden problems detected ⚠️ |

**Bias Gap: 79.8 percentage points**

---

## Key Findings

1. **End Users showed 2X more behavioral friction** (18.8 vs 9.3 cues per interview)
2. **But expressed similar verbal sentiment** to Admin users
3. **The audio revealed what the text concealed**

### Example: Frustrated Moments (End Users)

| Timestamp | Quote | Behavioral Cue |
|-----------|-------|----------------|
| 02:24 | "I can't tell if I selected it or not." | Frustrated tone |
| 03:06 | "Honestly, it's kind of confusing..." | Pause (4s) + vocal markers |
| 03:38 | "This is taking a while." | Frustrated tone |

**Yet in verbal summaries, these users described the experience as "generally positive."**

---

## Architecture

### High-Level System Design
```
┌─────────────────┐
│ Text Scripts    │
│ (50 interviews) │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Audio Files     │
│ (OpenAI TTS)    │
└────────┬────────┘
         │
         ▼
┌─────────────────────────┐
│ Gemini 3 Pro            │
│ (Audio-Direct Analysis) │
│ - Extract pauses        │
│ - Detect vocal markers  │
│ - Analyze tone          │
└────────┬────────────────┘
         │
         ▼
┌─────────────────────┐
│ Behavioral Cues     │
│ (559 cues extracted)│
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│ Neo4j Knowledge     │
│ Graph               │
│ - 50 Interviews     │
│ - 559 Cues          │
│ - 2 User Segments   │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│ Say-Do Consistency  │
│ Score Calculation   │
└─────────────────────┘
```

### Tech Stack

**Intelligence:**
- Gemini 3 Pro (`gemini-3.0-pro`) - Multimodal audio analysis
- OpenAI TTS (`tts-1`) - Synthetic audio generation

**Infrastructure:**
- Neo4j Aura - Knowledge graph storage
- Python 3.11+ - Analysis pipeline
- Google Cloud Run - Deployment (planned)

---

## Demo Video

🎬 **[Watch the 4-minute demo](#)** *(Link coming soon)*

See the full methodology in action, including:
- Live Neo4j graph queries
- Say-Do Score calculation
- Behavioral cue extraction examples
- Evidence of the 79.8 point bias gap

---

## White Paper

📄 **[Read the full methodology paper](#)** *(Link coming soon)*

Detailed explanation of:
- Theoretical foundation (Social Desirability Bias)
- Experimental design
- Results analysis
- Limitations & future work

---

## Limitations & Future Research

This is a **methodology validation study** with important limitations:

1. **Synthetic data only** - Real human validation needed
2. **English language only** - Cross-cultural generalization unknown
3. **Controlled TTS voices** - Natural speech variation not tested
4. **Single product domain** - B2B/Enterprise contexts may differ

**Next step:** Recruiting 20 research teams for CHI 2027 validation study across diverse populations and contexts.

---

## Example Output

**Sample behavioral cue extraction:**
```json
{
  "interview_id": "end_user_script_03",
  "behavioral_cues": [
    {
      "timestamp": "01:38",
      "type": "pause",
      "duration": "3 seconds",
      "context": "Before confirming selection"
    },
    {
      "timestamp": "02:24",
      "type": "frustrated",
      "quote": "I can't tell if I selected it or not.",
      "context": "Attempting to complete task"
    },
    {
      "timestamp": "03:06",
      "type": "vocal_marker",
      "quote": "Um, uh, this is kind of confusing",
      "context": "Navigation confusion"
    }
  ],
  "say_do_score": 3.2,
  "interpretation": "LOW CONSISTENCY - Hidden problems detected"
}
```

---

## Methodology Validation Study

**Seeking research collaborators for CHI 2027 paper.**

If you're a UX researcher or product researcher interested in validating this methodology:

📧 **[Sign up here](#)** *(Form coming soon)*

What's involved:
- Provide 1-2 real user research sessions (audio recordings)
- Receive CausalTrack analysis report
- Validate findings against your expert judgment
- Co-author credit on CHI submission (if desired)

**Target:** 20 research teams across diverse domains

---

## License

**Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**

You are free to:
- Use this methodology for academic research
- Share and adapt the approach
- Cite this work in publications

Under these terms:
- **Attribution required** - Credit this work appropriately
- **Non-commercial** - Not for commercial use without permission

For commercial licensing inquiries: kostas.kazakos@gmail.com

---

## Citation

If you use this methodology in your research:
```bibtex
@misc{causaltrack2026,
  author = {Kostas Kazakos},
  title = {CausalTrack: Audio-Based Behavioral Truth Detection for User Research},
  year = {2026},
  month = {February},
  url = {https://github.com/kgkazakos/causaltrack},
  note = {Methodology validation study}
}
```

---

## Acknowledgments

Built with:
- **Gemini 3 Pro** by Google DeepMind
- **Neo4j** graph database
- **OpenAI TTS** for synthetic audio

Inspired by decades of research on Social Desirability Bias and the Say-Do Gap in behavioral science.

---

## Contact

**Personal Research Project**  
Not affiliated with any employer.

📧 Email: kgkazakos@gmail.com  
💼 LinkedIn: [www.linkedin.com/in/kazakosk/](https://www.linkedin.com/in/kazakosk/)

---

**Last Updated:** February 23, 2026  
**Status:** Methodology Validation Phase  
**Next Milestone:** Scaled validation for academic conference