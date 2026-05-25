# Google's AI Control Center Is the Admin-Side Story to Pair With Every Gemini Enthusiasm Session

_Filed 25 May 2026._

> **Thesis:** Google's new AI control center is not a complete governance solution. It is a useful administrative map: it centralizes visibility, points administrators toward Gemini and Workspace data controls, and makes the security conversation harder to ignore. For international schools, the practical implication is straightforward: every staff-facing Gemini training session should be paired with a clear admin conversation about access, data sources, age settings, agent actions, logs, and student-data boundaries.

## 1. What Google has actually launched

Google announced the [AI control center in the Workspace Admin console](https://workspaceupdates.googleblog.com/2026/05/securely-manage-AI-and-agent-access-to-Workspace-data-with-the-AI-control-center.html) on May 4, 2026. It appears under **Generative AI > AI control center**, and Google describes it as a central dashboard for "generative AI and agent actions" across Workspace.

Google says the control center has four modules:

- **Monitor and control AI access:** links to Gemini usage reports and management settings. At launch, Google says it shows usage for Gmail, Drive, Docs, Sheets, Slides, Meet, Calendar, Chat, and the Gemini app.
- **Manage security for AI products:** product-specific settings, including Gemini in Meet and other AI surfaces.
- **Manage fundamental security:** classification labels, trust rules, data protection rules, and related controls that matter more once AI starts making cross-file inferences.
- **Review privacy, abuse, and compliance safeguards:** links to Google's privacy and compliance commitments.

The help page, last updated May 21, says the feature is supported for [Enterprise Standard and Enterprise Plus](https://knowledge.workspace.google.com/admin/gemini/explore-the-ai-control-center). Schools using Google Workspace for Education should therefore verify whether the exact dashboard is available in their tenant, rather than assuming that all related controls are exposed through the new control center.

That distinction matters. A training slide can say "Google has admin controls." The admin team needs to know which controls are actually present.

## 2. The real control surface is split across several places

The control center is useful because it gathers the signposts. But the governance itself still lives across multiple Admin console settings.

For **Gemini in Workspace apps**, admins can enable or disable Gemini features in Gmail, Calendar, Drive, Docs, Sheets, Slides, Forms, Drawings, Vids, Meet, Chat, and [Google Workspace Studio](https://knowledge.workspace.google.com/admin/gemini/manage-access-to-gemini-features-in-workspace-services). Google notes one important caveat: turning Gemini off in one app does not necessarily stop users from referencing that app's data through Gemini elsewhere. If Gemini is off in Drive, a user may still ask Gemini in Gmail about a Drive file they own.

For **Workspace Intelligence**, admins can control which data sources Gemini can actively search: Gmail, Drive/Docs, Calendar, and Chat. The default is on. The supported editions include Education Plus, Teaching and Learning add-ons, and Google AI Pro for Education. Turning off a source limits active search, but users can still point Gemini at specific files, emails, or Chat messages, and Gemini may use the currently open document as context. Google explains this in its [Workspace Intelligence admin help](https://knowledge.workspace.google.com/admin/gemini/control-workspace-intelligence).

For **the Gemini app**, admins separately control whether users can use gemini.google.com, mobile apps, Gemini in Chrome, and Gemini on Mac. Google also separates "core service" use, with enterprise-grade data protections, from "additional Google service" use, where chats may be reviewed by humans and used to improve Google services. That distinction in the [Gemini app admin page](https://knowledge.workspace.google.com/admin/gemini/turn-the-gemini-app-on-or-off) is not decorative. It changes the risk profile.

For **Gemini app access to Workspace services**, admins can allow Gemini to interact with Calendar, Docs, Drive, Gmail, Keep, and Tasks. Google says conversation history must be enabled for Workspace apps in Gemini, and disabling Workspace apps does not erase existing chats that used them. See [Control Gemini App access to Workspace services](https://knowledge.workspace.google.com/admin/gemini/turn-google-apps-in-gemini-on-or-off).

The school translation: "Gemini is on" is not a setting. It is a matrix.

## 3. Age, organizational units, and license status are not administrative trivia

For schools, the key questions are not merely "Is Gemini available?" They are:

- Which organizational units are staff?
- Which organizational units are students?
- Which accounts are marked under 18?
- Which users have Education Plus, Teaching and Learning, Google AI Pro for Education, or other AI access?
- Which features behave differently for under-18 users?

Google says Workspace Intelligence is not available to Google Workspace for Education users under 18. It also says that if Workspace Intelligence is enabled for an over-18 user, it can access content shared with that user even when the sharing user does not have Workspace Intelligence access. In practice, student-created or student-shared content may become part of an adult user's AI context if the adult already has permission to view it.

NotebookLM has its own age matrix. Google says [NotebookLM is part of its education AI quick-start guidance](https://knowledge.workspace.google.com/admin/getting-started/editions/quickstart-guide-to-gemini-and-notebooklm-for-education), with feature exceptions by age. Under-18 users can use NotebookLM access, Audio Overviews, flashcards, quizzes, reports, sources, Video Overviews, and chat, while features such as Deep Research, infographics, and slides are listed for 18-and-over users. Google also says that when users import Drive files into NotebookLM, NotebookLM creates a new copy stored with the user's NotebookLM data, not in Drive; Drive sharing and data region settings do not apply to that NotebookLM copy.

Workspace Studio is also school-relevant. Google includes [Workspace Studio access among the Gemini controls for Workspace services](https://knowledge.workspace.google.com/admin/gemini/manage-access-to-gemini-features-in-workspace-services), while users designated under 18 cannot use AI features in Studio. Admins can turn it on or off by organizational unit or access group. Because Studio creates flows that automate cross-Workspace tasks, it should be treated less like "another Gemini button" and more like a no-code agent builder.

Before broad staff training, schools should have an organizational-unit, age, and licensing table in hand. Not perfect. Just explicit. Otherwise every workshop begins with a governance shrug.

## 4. Logging is better than it was, but still not the same as understanding

Google now provides several layers of AI visibility:

- [Gemini usage reports](https://knowledge.workspace.google.com/admin/gemini/review-gemini-usage-in-your-organization) show organizational and user adoption, active users, app-level usage, users hitting feature limits, and usage by content type. Reports can be filtered by organizational unit or group.
- [Gemini for Workspace log events](https://knowledge.workspace.google.com/admin/reports/gemini-for-workspace-log-events) can show actor, app, event category, feature source, timestamp, and action type. Event categories include conversations, generate, summarize, inactive, and unknown.
- Google's 2025 update says Gemini audit logs are available via the Reports API and in the audit/security investigation tools, allowing admins to track adoption, feature utilization, app-level usage, and last-used timestamps. See [Access Gemini Audit logs](https://workspaceupdates.googleblog.com/2025/07/gemini-audit-logs-reporting-api-audit-and-security-invesitgation-tools.html).
- [Workspace Studio log events](https://support.google.com/a/answer/16703097?hl=en-CA) go further for flows: create, view, edit, delete, turn on/off, start/end runs, step app, step name, run type, errors, and reasons a flow was turned off.

That is useful. It is not omniscience.

The visible logs can tell administrators that a user summarized, generated, created a flow, or used Gemini in a particular surface. They may not provide a clean narrative of exactly what sensitive information influenced an answer, whether the answer was pedagogically appropriate, or whether a user pasted confidential data into the wrong AI surface.

The better move is preventative: classification labels, Drive sharing hygiene, trust rules, data protection rules, and staff norms before large-scale usage. Logs are the smoke alarm, not the building code.

## 5. What schools should ask before the next Gemini session

Here is the concrete pre-training checklist for school technology teams and Ed Tech Coaches:

- **Edition reality:** Does the tenant actually have the new AI control center, or only the underlying Gemini controls?
- **Organizational-unit status:** Which staff and student organizational units have Gemini app access, Gemini in Workspace apps, Workspace Intelligence, NotebookLM, and Workspace Studio?
- **Age classification:** Are under-18 settings correct for student accounts, test users, shared accounts, and service accounts?
- **Gemini app vs Workspace Gemini:** Is gemini.google.com operating as a core service for staff, or are any users falling into "additional Google service" terms?
- **Workspace apps in Gemini:** Can Gemini access Gmail, Drive, Docs, Calendar, Keep, and Tasks? Is conversation history required and enabled? Who can delete conversations, and what is the auto-deletion period?
- **Workspace Intelligence sources:** Are Gmail, Drive/Docs, Calendar, and Chat all active sources? If any are off, do staff understand that specific files or currently open documents can still be used?
- **NotebookLM:** Is NotebookLM on for staff, students, or both? Do staff understand that imported Drive files are copied into NotebookLM storage, where Drive sharing and data region settings do not apply?
- **Workspace Studio:** Is Studio on? Who can create flows? Are third-party services allowed? Who reviews flows that send email, post to Chat, or move Drive content?
- **Audit visibility:** Who can access Gemini reports, Gemini log events, Workspace Studio log events, and security investigation tools? Is anyone reviewing them on a schedule?
- **Data protection:** Are classification labels, data protection rules, trust rules, external sharing rules, and Context-Aware Access configured well enough for AI to sit on top of them?
- **Training line:** What are staff explicitly allowed to try in a Gemini session, and what examples are off-limits because they touch student data, safeguarding, health, HR, assessment accommodations, or confidential family communication?

The comparison point with OpenAI is useful only as market signal. OpenAI's Enterprise/Edu release notes say connectors and apps are disabled by default, can be enabled by admins, and can be controlled through RBAC and action-level settings; new connector actions are disabled until approved. See [ChatGPT Enterprise & Edu release notes](https://help.openai.com/en/articles/10128477-chatgpt-enterprise-edu-release-notes). That is the direction of travel: serious AI platforms are moving toward admin-visible connectors, role-based access, and action controls. Google's difference is that its AI is embedded directly inside the productivity suite schools already use. That makes the blast radius quieter.

The practical line for schools is not "slow down AI adoption." It is: make adoption administratively honest before the enthusiasm outruns the controls.
