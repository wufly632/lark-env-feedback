# Lark Env

**Publisher: wufly · Free to use · Proprietary / closed source**

Load environment variables from a Feishu/Lark cloud document before local Java Run/Debug in IntelliJ IDEA.

This repository contains **public documentation, legal notices and the issue tracker only**. It does not contain plugin source code. Lark Env is an independent third-party tool, not affiliated with or endorsed by Feishu/Lark or JetBrains.

> Marketplace publication is being prepared. This page is not a claim that the plugin has been approved or listed yet.

## Requirements / 使用前提

- IntelliJ IDEA **2026.2.x (build 262)** with Java support.
- A separately installed `lark-cli`, authenticated as a user who can read the selected document.
- Local **Application / Spring Boot** run configurations.
- Windows must use the native `lark-cli.exe`, not the npm `.cmd` or `.ps1` shim.

Maven/Gradle delegated execution, JUnit, remote targets, and offline mode are not supported in this version. Compatibility validation has been performed against IDEA 2026.2.1; other IDE series are not claimed to be supported.

## Quick start / 使用方法

1. Install Lark Env from an available publisher-provided plugin ZIP via **Settings → Plugins → Install Plugin from Disk**. Follow any restart prompt.
2. Create a unique heading in your Feishu document, for example `app-dev`, with a single code block below it:

   ```dotenv
   SPRING_PROFILES_ACTIVE=local
   APP_HOST=127.0.0.1
   APP_PORT=8080
   ```

3. Open **Settings → Tools → Lark Env**.
4. Enable for the current project. Enter the document URL and exact heading text.
5. Leave run configuration names empty for all supported configurations in this project, or enter exact names, one per line.
6. Use **Test Read** and save the settings, then Run or Debug.

配置标题指文档正文的标题，不是文档文件名；标题下需要恰好一个代码块。运行配置名称可留空，留空只影响当前项目。代码块高亮语言不影响解析。

The plugin reloads on every launch. Existing IDEA launch variables override document variables. Retrieval failure, timeout, invalid format, or cancellation stops the launch rather than silently falling back to cached values.

## Configuration format

Supports `KEY=value`, optional `export `, empty values, single/double quotes, full-line comments, and whitespace-prefixed inline comments. Duplicate keys and malformed values are rejected. No shell execution, variable interpolation, multiline values, or quoted escape processing is performed. Nested tables, embedded sheets and attachments are not configuration sources.

## Security and privacy

- Do not store production secrets in ordinary cloud documents.
- Restrict document editing: an editor can change runtime configuration.
- The plugin fetches the document via the local CLI and selects the section in memory; content outside the selected section may be retrieved.
- The plugin does not intentionally persist variable values or send document contents to wufly.
- CLI credentials/logging, the launched application's logs, IDE diagnostics and OS memory dumps are outside the plugin's control.
- Launch retrieval is bounded by a timeout but currently occurs within IDEA's launch read action; slow networks may delay IDE actions requiring a write lock.

Read the [Privacy Notice](PRIVACY.md) and [End User License Agreement](EULA.md).

## Feedback / 问题反馈

[Open an issue](https://github.com/wufly632/lark-env-feedback/issues/new/choose) for bugs or feature requests.

Please provide the plugin version, IDEA version, operating system, launch type, steps to reproduce, and a sanitized error message.

**Issues are public. Never upload `.env` files, real environment-variable values, tokens, passwords, private document URLs, internal project screenshots, or unredacted logs. Use dummy values in reproduction examples.**

涉及隐私或安全问题时，不要直接公开敏感信息。可先发一个不含敏感细节的请求，由发布者安排私下沟通方式。

## Changelog

- **0.1.3**: Fix the read-action / synchronous UI dispatch error during launch.
- **0.1.2**: Make run configuration names optional; blank means all supported configurations in the current project.
- **0.1.1**: Ignore code-block syntax highlighting labels during dotenv parsing.

## License

Version 0.1.3 is free for personal and internal business use under the proprietary [EULA](EULA.md). No plugin source-code license is granted. Third-party dependencies retain their own licenses.
