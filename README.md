# translation-guardrail

Prompt "guardrails" for fixing machine-translated subtitles (SRT) on Red Hat OpenShift/Kubernetes training videos, plus companion glossaries that pin down which technical terms must stay in English. Currently covers **Japanese (JA)** and **Korean (KO)**.

## What's in this repo

| File | Purpose |
| :--- | :--- |
| [subtitle_localization_guardrail_ja.md](subtitle_localization_guardrail_ja.md) | The main prompt for EN → JA subtitle QA. Paste this into Gemini to start a correction session for Japanese SRT files. |
| [subtitle_localization_guardrail_ko.md](subtitle_localization_guardrail_ko.md) | The main prompt for EN → KO subtitle QA. Paste this into Gemini to start a correction session for Korean SRT files. |
| [kubernetes_openshift_glossary_common.md](kubernetes_openshift_glossary_common.md) | Language-neutral glossary: the full list of Kubernetes/OpenShift terms that must never be translated, with justification. Referenced automatically by both guardrail files — you don't paste this one yourself. |
| [kubernetes_openshift_untranslated_terms_ja.md](kubernetes_openshift_untranslated_terms_ja.md) | Japanese-specific addendum to the common glossary (example sentences, JA subtitle conventions). |
| [kubernetes_openshift_untranslated_terms_ko.md](kubernetes_openshift_untranslated_terms_ko.md) | Korean-specific addendum to the common glossary (particle/case-marker rules, example sentences). |

Each guardrail file links to its matching glossary addendum, which in turn defers to the common glossary — you only need to open the one guardrail file that matches your target language; it references everything else on its own.

## Workflow: improving subtitle quality on an existing video

1. **Export the SRT files from the video system.**
   Download both the **English SRT** (source) and the **raw, machine-translated target-language SRT** (e.g. Japanese or Korean) for the video you want to fix.

2. **Start a new chat using the Gemini Thinking model.**
   In the Gemini Web App, select the **Gemini Thinking** model before starting the chat — the guardrail's multi-step reasoning (detecting ASR errors, cross-checking the glossary, reconciling timing between the English and target-language SRTs) benefits from the extended reasoning this model provides.

3. **Upload both SRT files to Gemini.**
   Attach the English SRT and the target-language SRT to the chat.

4. **Start the correction session with the matching guardrail file.**
   Open the guardrail file for your target language on GitHub:
   - Japanese → [subtitle_localization_guardrail_ja.md](subtitle_localization_guardrail_ja.md)
   - Korean → [subtitle_localization_guardrail_ko.md](subtitle_localization_guardrail_ko.md)

   Copy the **entire contents** of that file and paste it into the same Gemini chat as your first message (after or alongside the uploaded SRT files). This initializes Gemini with the correction rules, tone requirements, and the untranslatable-terms glossary.

5. **Wait for the handshake, then let Gemini process the files.**
   Gemini will reply with the handshake phrase ("Ready for the SRT file.") to confirm it has loaded the guardrail, then generate:
   - **Output 1** — the corrected target-language SRT, shown inline in the chat **and** opened in Canvas as a downloadable `.srt` file.
   - **Output 2** — an English QA feedback report summarizing what was fixed (mistranslations, ASR errors, unit/terminology issues, tone, and — for Korean — particle errors).

6. **Download the corrected SRT from Canvas.**
   Use Canvas's download/export option to save the corrected subtitle file to your machine.

7. **Re-import the corrected SRT into the original video.**
   Replace the raw machine-translated subtitle track on the source video with the corrected `.srt` file to improve the subtitle quality of the published video.

## Notes

- The guardrail files are written as **prompts for a generative AI model** (Gemini), not as scripts to execute. "Using" a file means pasting its content into the chat, not running it.
- Use the **Gemini Thinking** model, not a standard/fast model — the guardrail relies on multi-step reasoning across the glossary, ASR-error detection, and (for Pattern 3) timing reconciliation between two SRT files.
- If you only have the target-language SRT (no English source), the guardrail still works — see Pattern 2 in each guardrail file's "Inputs and Outputs" section.
- The Canvas download step assumes the Gemini Web App (gemini.google.com). Other Gemini surfaces (API, AI Studio) don't have an equivalent built-in download mechanism.
