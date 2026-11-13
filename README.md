# AI agent skills

Small, reusable prompts and skills for AI agents. Each skill lives in its own directory and describes the desired behavior without requiring a particular agent framework.

| Skill | What it does |
| --- | --- |
| [agent-pager](agent-pager/SKILL.md) | Guides you through setting up ntfy so your agent can get your attention on your phone, including persistent ringing on Android, only for situations you choose. |

## Use a skill

**Paste-in setup:** Open the skill's `SKILL.md`, select **Raw**, and copy its full contents into your agent's conversation. Ask it to guide you through setup. The metadata at the top can stay. The instructions are self-contained; no separate prompt is required.

**Installable skill:** If your agent supports the [Agent Skills format](https://agentskills.io/specification), install or copy the individual skill directory using that agent's documented procedure, then ask it to use the skill. Installation paths and invocation syntax vary between agents.

Review instructions before using them. A skill does not give an agent tools, permissions, persistent memory, or background execution that it does not already have.

## agent-pager

An optional phone-paging channel alongside your agent's existing messages and notifications. It does not automatically redirect ordinary questions, task-completion updates, or permission prompts to ntfy.

- **Baseline:** Android and the official [ntfy.sh](https://ntfy.sh) service, using a free, unreserved topic with a cryptographically random suffix. No account is required for this baseline.
- **Setup:** Choose when to page, quiet hours, message detail, topic prefix, and display name; install ntfy; test delivery; configure and test ringing; save the agreed policy in the agent's own persistent configuration.
- **Default message detail:** Concise information about the actual issue or deadline and the action needed. For example, “I can't access XYZ, so deployment is blocked. Please restore access.” Secrets and sensitive details are excluded.
- **Persistent ringing:** Android repeats the selected notification sound until dismissed when ntfy's highest-priority alert setting is enabled. Send the first urgent test before choosing its sound in Android settings, so the relevant notification category exists.
- **Requirements:** An agent that can make outbound HTTPS requests, and an Android phone with ntfy and notification permission. Ongoing use also requires a way for the agent to retain and apply the paging policy. No additional server, daemon, or MCP integration is required by this skill.
- **Other environments:** The agent confirms your platform and hosting preference. It may adapt for iPhone or self-hosting after checking current documentation; the Android ringing behavior must not be assumed elsewhere.

The Android + ntfy.sh setup was manually tested: normal notification delivery and priority-5 sound repetition until dismissal. Other phone configurations and agent frameworks have not all been tested. Installing this skill does not itself create deadline monitoring or a background service.

### Privacy

Treat pages as **semi-private**, not as a secure messaging channel. An unreserved topic is a shared secret: anyone who learns it can subscribe or publish. HTTPS protects transport, but the standard service is not end-to-end encrypted; the service operator can access message contents. Notifications may appear on the lock screen. Never commit real topic URLs, tokens, or personal paging configuration to this repository. Generate a new secret for each setup; rotate it if exposed.

### Disclaimer — use at your own risk

These prompts, skills, examples, and instructions are provided **“AS IS” and “AS AVAILABLE,” without warranties of any kind**. You are responsible for reviewing them, configuring your agent and devices, protecting credentials, testing behavior, and deciding whether they are suitable for your use.

AI agents may misunderstand instructions or act incorrectly. Notifications may be delayed, duplicated, missed, or disclosed; phone settings, networks, third-party services, and software changes can affect behavior. **Do not rely on this project for emergencies, life-safety use, or as the sole means of receiving critical alerts.** There is no guarantee of delivery, timeliness, privacy, accuracy, compatibility, or continued availability.

To the maximum extent permitted by applicable law, the authors and contributors disclaim liability for claims, damages, losses, or other liability arising from the use of, or inability to use, this project. See the [MIT license](LICENSE) for the full warranty and liability terms. This project is independent of ntfy and any agent platform.

## Adding more skills

Use a descriptive, lowercase directory name with hyphens and a `SKILL.md` containing `name` and `description` metadata followed by instructions. Keep small skills self-contained. Add scripts or reference files only when needed, and list the skill in the table above. Use placeholders in examples; keep personal configuration outside the repository.

## License

[MIT](LICENSE). Copyright (c) 2026 arjver.
