# agent-pager

**An opinionated but configurable phone pager that adapts to your agent or harness.**

Give your agent a way to get your attention when it matters. Paste in the setup instructions or install them as a skill, and your agent walks you through choosing when to page, configuring your phone, testing the alerts, and saving the policy using its own supported mechanisms.

The baseline is **Android + [ntfy.sh](https://ntfy.sh)**, with persistent ringing for the situations you choose. It works alongside existing channels such as Telegram or your agent app's notifications. Installing it does not mean every completed task, question, or permission request should ring your phone.

## Quick start

### Give your agent this prompt

Copy and paste:

```text
Open https://github.com/arjver/ai-agent-skills/blob/main/agent-pager/SKILL.md,
read the complete agent-pager skill, and use it to help me get set up.
Guide me through the setup interactively, confirm my preferences, and
adapt it to your tools and harness. Preserve my existing notification
channels and save the agreed paging policy using your supported
persistent configuration. If you cannot access the file, ask me to
paste its contents.
```

You can add what you already know you want, such as: “I use Android and only want persistent ringing for very urgent things. Keep routine updates in Telegram.” The agent should read the instructions and begin the guided setup.

The agent needs access to the repository to fetch the link. If it is private, use an authorized GitHub connection or the paste-in fallback below; do not share access tokens in the prompt.

### Or paste the full skill

1. Open [SKILL.md](SKILL.md), select **Raw**, and copy the entire file into your agent's conversation. The metadata at the top can stay.
2. Tell it what you want, for example: “Help me set this up. I use Android and want persistent ringing only for very urgent things. Keep routine updates in Telegram.”
3. Follow its guided setup and phone tests.

The file is self-contained. You do not need to paste this README or install an extra server. Copying the instructions works even if the agent cannot fetch this repository.

### Install it as a skill

If your agent or harness supports the [Agent Skills format](https://agentskills.io/specification), install the **`agent-pager` directory** using its documented installation procedure. Then ask it to use `agent-pager` to set up paging. Paths and invocation syntax vary; there is no universal installation command.

`SKILL.md` contains the agent instructions; this README is for people. The README is optional supporting documentation and does not need to be loaded during each alert.

## Opinionated defaults, your decisions

The skill starts with a practical setup, then confirms your preferences. Defaults are recommendations, not permission to send alerts before you agree on when to use them.

| Area | Starting point | What you decide |
| --- | --- | --- |
| Platform and service | Android + official ntfy.sh | Confirm this, or ask the agent to adapt for iPhone or self-hosting after checking current capabilities. |
| Purpose | An extra channel for events that need attention | Which events qualify; which stay in existing channels. |
| Alert behavior | Persistent ringing for agreed urgent events | Ringing, ordinary notifications for selected events, or a combination. |
| Message detail | Concise, specific context and the next action | Less detail or additional privacy exclusions. |
| Naming | `<agent-name>-<random-secret>` and a friendly display name | Prefix and display name, confirmed during setup. |
| Quiet hours | Ask rather than assume | Anytime paging or a schedule, timezone, and exceptions. |
| Repeated pages | One page per incident; the phone repeats the sound | Any intentional escalation or repeat policy. |
| Integration | Use the agent's existing capabilities | How preferences are stored and applied by that agent. |

For message content, the default is closer to:

> I can't access XYZ, so deployment is blocked. Please restore access.

or:

> Your assignment is due in 1 hour and is still not submitted. Please check the course portal.

The agent confirms your preferred level of detail with a sample. Secrets and sensitive information are excluded, and uncertain facts must be phrased as uncertain. These examples do not automatically authorize deployment alerts, assignment monitoring, or access to new services.

## What setup covers

1. **Agree on a paging policy.** Confirm platform, existing channels, qualifying events, message content, quiet hours, and requested behavior.
2. **Create a recognizable secret topic.** Confirm the prefix and display name, generate a fresh 128-bit random suffix, and guide installation of the official ntfy app. Provide a subscription link plus copyable manual instructions, because some chat apps do not open `ntfy://` links correctly.
3. **Test ordinary delivery.** Send one normal setup test and confirm it actually appears on the phone.
4. **Configure ringing if requested.** Enable “Keep alerting for highest priority,” send a priority-5 test, then customize the sound. The first urgent notification may be needed before its Android notification category appears in settings. Test again with the chosen sound and the phone locked.
5. **Test additional behavior as needed.** Silent mode and Do Not Disturb require their own configuration and checks; priority 5 alone is not a promise to bypass either.
6. **Save and connect the policy.** Use the agent's supported private configuration and persistent instructions or event handling. Report how future sessions will apply the rules and any remaining limitations.

This is a notification that can repeat a sound, not a telephone call or voice conversation. Dismiss the notification to stop ringing. Reply through your existing agent conversation; dismissing it does not communicate approval or acknowledgment to the agent.

## How it adapts to your agent

The skill specifies the behavior to achieve, not a required framework implementation. An agent may use its own HTTP client, private configuration, durable memory, instructions, or hooks. It should inspect the capabilities it actually has and use existing conventions instead of installing a new stack by default.

For example, an agent already using Telegram can keep routine conversation there and use ntfy only for the agreed pages. A coding harness can retain its ordinary approval workflow while paging for specifically agreed blockers. An agent without durable storage should explain that limitation instead of claiming the setup will survive a new session.

Saving a topic is not sufficient: the agent also needs a reliable way to find and apply your paging policy later. The skill asks it to verify that integration. **It does not itself provide background execution, deadline monitoring, or new permissions.** If you want those, your agent must support and configure them separately with your agreement.

## Requirements, cost, and compatibility

- An Android phone with the official ntfy app and notification permission.
- An agent that can send outbound HTTPS requests. Ongoing paging also needs a supported way to retain and apply the agreed policy.
- Connectivity on both sides, suitable Android notification settings, and testing on your own device.

The baseline uses a free, unreserved ntfy.sh topic, with no account or paid plan required. Agent-provider costs and the service's limits still apply. No additional daemon, MCP server, or self-hosted server is required by this skill.

The Android + ntfy.sh flow was manually tested for normal delivery and priority-5 sound repetition until dismissal. Compatibility with every agent, phone, battery setting, or operating-system version is not guaranteed. iPhone and self-hosted variations need current documentation and their own tests; do not assume the same ringing behavior.

## Privacy and security

Treat pages as **semi-private**, not secure messaging. Anyone who learns an unreserved topic can read or publish to it. A descriptive prefix makes the topic recognizable; the cryptographically random suffix makes it hard to guess.

HTTPS protects transport, but the standard ntfy service is not end-to-end encrypted: the server operator can access contents, and notifications may be visible on the lock screen. Do not include passwords, tokens, recovery codes, private message excerpts, or sensitive personal/business details. Keep private discussion in your existing appropriate channel.

Store the real topic and configuration privately, outside this repository. Do not paste them into public issues or examples. If the topic leaks, generate a new secret, update both phone and sender, and test again. Switching topics does not erase old messages or revoke access to the old topic.

## Change or disable it

Ask your agent to update `agent-pager` preferences: triggers, content detail, quiet hours, display name, or alert behavior. It should retain the existing topic unless a change requires replacing it.

To stop paging, ask the agent to disable it and remove any paging-specific integration it created. You can also mute or unsubscribe in ntfy, but that alone does not stop the sender from publishing. Existing conversation channels should remain intact.

## Limitations and disclaimer

**Use at your own risk.** This skill, its examples, and its instructions are provided **“AS IS” and “AS AVAILABLE,” without warranties of any kind**. You are responsible for reviewing the instructions, configuring your agent and devices, protecting credentials and data, testing behavior, and deciding whether this is suitable for your use.

AI agents may make mistakes; notifications can be delayed, duplicated, missed, or disclosed. Phone settings, networks, third-party services, and software changes can affect behavior. Server acceptance does not prove your phone received an alert or that you heard it. No delivery, timeliness, privacy, accuracy, compatibility, or reliability guarantee is provided.

**Do not rely on this for emergencies, life-safety use, or as your only critical-alert channel.**

To the maximum extent permitted by applicable law, the authors and contributors disclaim liability for claims, damages, losses, or other liability arising from use of, or inability to use, this skill.

## License

[MIT](../LICENSE).

## References

- [Agent instructions](SKILL.md)
- [ntfy mobile setup and download links](https://docs.ntfy.sh/subscribe/phone/)
- [Publishing and priority settings](https://docs.ntfy.sh/publish/)
- [ntfy security model and FAQ](https://docs.ntfy.sh/faq/)
- [Self-hosting configuration](https://docs.ntfy.sh/config/)
