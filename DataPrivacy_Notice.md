## ⚠️ Privacy & safety — read before sharing any health data

Lab results are medical records. Before sharing them with any AI tool — including Claude — it is worth taking time to understand what the risks actually are, where your data goes, and how to protect yourself.

### The core problem: AI chatbots are not covered by HIPAA

HIPAA — the Health Insurance Portability and Accountability Act — restricts how hospitals, insurers, and healthcare providers handle your medical data. It does not apply to AI companies. When you share a lab report with Claude, ChatGPT, Perplexity, or any other consumer AI chatbot, you are outside the legal protections that govern your doctor's office or your insurance company. The company's own privacy policy is the only thing governing what happens to your data, and those policies vary widely and can change.

The risks fall into a few categories.

### Risk 1: Training data

Most AI companies reserve the right to use conversations to improve their models, unless you explicitly opt out. If you paste your lab results into a chat without opting out, those values — potentially alongside other things you've shared in the conversation — could become part of future training data. Even if individual data points seem innocuous, aggregated health conversations at scale can reveal sensitive patterns.

### Risk 2: Data breaches and retention

Your conversation is stored on the AI company's servers for some period of time — sometimes indefinitely unless you manually delete it. AI companies are increasingly high-value targets for data breaches. Health data is particularly sensitive because, unlike a compromised password, you cannot change your blood values or your medical history.

### Risk 3: Re-identification from "anonymous" data

It is a common misconception that removing your name from a lab report makes it anonymous. Research has repeatedly shown that health data can be re-identified with surprisingly little additional information — your age, zip code, and a handful of biomarker values can be enough to narrow down your identity, particularly in smaller populations. 

### Risk 4: No guarantee of accuracy

AI models can misread, misparse, or misattribute lab values, especially from PDFs, screenshots, or non-standard lab formats. An error in parsing is usually obvious (a missing value), but a subtle numeric error — transposing digits, for example — could go unnoticed and affect how you interpret your trends over time. 

### Risk 5: Secondary use by third parties

Some AI platforms share data with third-party partners for analytics, advertising, or product improvement purposes. Even if the primary AI company has a reasonable policy, data passed to downstream vendors may be subject to less stringent terms.

---

### What counts as protected health information (PHI)

PHI is any information that could identify you alongside a health detail. In a typical lab report this includes your full name, date of birth, address, phone number, patient ID or account number, ordering physician's name, the name and address of the lab or clinic, insurance information, and the date of service.

The numeric lab values themselves — a number like "WBC: 5.6" — are not inherently identifying on their own. The risk comes from combining them with identifiers, and from aggregating enough data points that re-identification becomes possible.

---

### Best practices before sharing lab data with any AI

**Remove all identifying information before pasting or uploading.** Delete your name, date of birth, patient ID, doctor's name, and lab facility name before sharing anything. Replace them with placeholders like `[REDACTED]` or simply delete them. The numeric values and marker names are all this tracker needs.

**Do not upload raw PDF lab reports.** PDFs from labs almost always contain your full name, date of birth, address, account number, and ordering physician embedded in the document header, footer, and metadata — even if they are not visible on screen. Uploading a PDF hands the AI company the entire file. Instead, copy and paste only the values section as plain text after reviewing it for identifiers.

**Crop screenshots carefully.** If you take a screenshot of your results, crop it to show only the values table. Lab report headers typically contain your name, DOB, patient number, and the ordering physician's details — none of which the tracker needs.

**Opt out of model training before you start.** On claude.ai: **Settings → Privacy → turn off conversation training**. On other platforms, look for equivalent settings — they are not always easy to find.

**Delete conversations when you are done.** Don't leave conversations containing health data sitting in your chat history.

**Only share what you need.** You can manually type in only the markers you want to track and leave everything else out. The tracker works fine with partial data.

**Treat AI output as a starting point, not a source of truth.** Always verify parsed values against your original report.

---

### Further reading

The risks of sharing health data with AI tools are an active area of public concern and ongoing reporting. The following resources provide useful context:

- KFF Tracking Poll — *Privacy Concerns and Uploading Personal Medical Data to AI* (2024): [kff.org](https://www.kff.org/public-opinion/kff-tracking-poll-on-health-information-and-trust-use-of-ai-for-health-information-and-advice/#c828efc6-7c8a-4a17-bf44-8a391004ee26--h-privacy-concerns-and-uploading-personal-medical-data-to-ai)

- Wall Street Journal — *Your Health Data and AI Chatbots*: [wsj.com](https://www.wsj.com/tech/ai/health-data-perplexity-claude-ai-d792a2df?mod=Searchresults&pos=1&page=1)

- New York Times — *Should You Share Your Medical Records with a Chatbot?* (December 2025): [nytimes.com](https://www.nytimes.com/2025/12/03/well/medical-records-chatbots.html)

---
