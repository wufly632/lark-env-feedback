# Lark Env Privacy Notice

Publisher: wufly
Applies to: Lark Env 0.1.3

Lark Env is an independent third-party IDEA plugin. It is not affiliated with or endorsed by Feishu/Lark or JetBrains.

## Data processed

When you test a configuration or launch an applicable run configuration in an enabled project, the plugin invokes your locally installed lark-cli as your authenticated user. The CLI requests the selected Feishu/Lark document. The plugin retrieves the document into memory, locates the configured heading, parses its environment-variable code block, and injects those variables into the application's process environment. The retrieval can include document content outside the selected section.

The plugin does not receive your login password or implement its own OAuth token storage. CLI credentials, profiles, authorization, logging, and external network behavior are managed by lark-cli under its own terms and privacy practices.

## Local storage and diagnostics

The plugin stores project-local configuration metadata in IDEA's workspace settings: enabled state, CLI executable path, document URL/token, selected heading, run configuration names, and timeout. A document URL/token can itself be sensitive metadata. Protect your workspace files.

The plugin does not intentionally persist document bodies or environment-variable values to files, run configuration XML, or a disk cache. It does not log those values; test-read feedback shows a variable count. Values remain in memory as needed for the request and launch, and in the launched process environment for its lifetime. No immediate secure memory erasure is guaranteed.

The plugin does not implement publisher-operated telemetry, analytics, or an upload service. It does not send document contents to wufly. IDE diagnostics, Marketplace services, local CLI behavior, application logs, debugging tools, and operating-system crash dumps are outside the plugin's control.

## Controls

Disable Lark Env for the project to stop future automatic launch reads; do not use Test Read if you do not want a manual request. Remove saved plugin settings to remove the local metadata. Manage and revoke CLI authorization separately. Disabling or uninstalling the plugin does not erase data already accessed by external services or the launched application and does not revoke your CLI login.

Restrict document read and edit permissions. A document editor can alter runtime configuration. Avoid storing production secrets in ordinary cloud documents.

## Contact

For general support and privacy questions, use https://github.com/wufly632/lark-env-feedback/issues. Issues are public: do not include personal data, passwords, access tokens, private document URLs, or unredacted logs. If a question requires confidential details, first request a private contact method without including those details.

When you post an issue, GitHub processes your account information and report under its own terms and privacy policy. wufly can see and respond to the public information you submit.
