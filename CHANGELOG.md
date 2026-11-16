# Changelog

What changed in each Lupyd release, newest first. Also at https://www.lupyd.com/changelog/. Downloads are on each [release](https://github.com/lupyd/lupyd/releases) and at https://www.lupyd.com/download/.

## 1.1.9 (2026-11-16)

Messages sit side by side with your chats on wider screens, a message that can't be sent says so, and activity notifications work.

### New

- On a wide screen, the open chat sits next to your list of chats. Esc closes it, Alt+Up and Alt+Down move to the chat above or below, and each chat keeps the text you hadn't sent yet. The search bar stays above the open chat, and Ctrl+K searches without leaving it.
- A message that the server keeps refusing shows Retry and Delete instead of waiting forever. A message written while you are offline, or while Lupyd is being updated, still goes out once the connection is back.
- Read ticks are remembered after restarting the app.
- In a call you can pick which microphone to use, and leaving asks first.
- Removing your profile photo, and other actions that can't be undone, ask first.

### Fixed

- The menu on a message opens from its own button and stays next to the message while the chat scrolls.
- A chat you have open on screen no longer counts its new messages as unread; one in a window you aren't looking at does.
- With no other device on your account, a chat no longer says older messages are on your other devices.
- Activity notifications (follows, likes, comments) load; before, they always failed to.
- The back button closes an open image instead of leaving the page.
- Messages you send or receive while older ones are loading no longer end up under the message box.

### Removed

- The "Require Two-Factor Verification" switch in Settings is gone. Two-factor sign-in isn't available yet, and the switch never turned it on.

## 1.1.8 (2026-11-15)

Your sign-in is kept in your system's keychain, notifications no longer show message text unless you ask, and a round of security fixes.

### New

- On Linux, macOS and Windows, the app keeps your sign-in in the system keychain instead of its own files, and its data folder is readable only by you. Existing sign-ins move over on the first start; if the keychain is unavailable, you stay signed in.
- Notifications say "New message" instead of showing the text. Turn the text back on in Settings, Privacy.
- The Android and iOS apps no longer link to plan checkout; plans are managed on the Lupyd website.

### Fixed

- The menu on a message (reply, edit, delete, react) is no longer cut off or dimmed in a band across the chat.
- Link previews, when turned on, only load public websites, never addresses on your own network.
- Opening a link can't start or answer a call by itself.
- Attachments only load from Lupyd's storage, and an uploaded file can't overwrite someone else's or run as part of lupyd.com.
- Shared files on Android can't reach the app's own private files.
- Groups: tighter rules on who can change roles, re-add devices, and send messages to a group, and a wrong history key sent first no longer hides the right one.
- A newly signed-in device trusts your account's other devices only provisionally until one of them confirms it.
- Signing in right after a server update no longer fails, and choosing a username no longer times out.
- A user you blocked can't follow you again.

## 1.1.7 (2026-11-14)

A new device has to be approved before it sees your messages, and groups are harder to break or take over.

### New

- When a new device signs in to your account, your other devices ask whether to trust it. Until you approve it on one of them, it gets none of your message history and can't unlock your chat backup. Settings, Devices shows which devices are trusted, and you can change it there.
- Group messages that came from another member's copy of the history, rather than straight to your device, are marked Unverified.
- Link previews are off by default, because loading one tells the linked site your IP address. Turn them on in Settings, App Preferences.

### Fixed

- Only the group owner can remove the owner's devices or change the owner's role, so a group can't lose its owner while they are away.
- A broken change sent to a group by one member no longer leaves everyone else stuck: it is withdrawn and the group carries on.
- A device whose clock was off, or that was offline for a long time, can catch up with its groups again instead of being stuck.
- Setting a member back to the default role now works (for the group owner). Before, it said it worked but changed nothing.
- Imported history can no longer claim to come from someone who didn't send it.
- A trust prompt for a device you then removed no longer stays on screen.
- Bios are limited to 4096 bytes.

### Web

- Signing in for a plan hands your session to the billing page without putting it in the page address, and cancelling a plan asks in the page itself.

## 1.1.6 (2026-11-13)

You choose which device to sign out when your account is full, and AI agents can join your chats.

### New

- When your account already has 5 devices, a new one no longer signs out an older device on its own. It asks you which one to sign out, showing each device's name and when it was last active, and is added once you choose.
- Settings, Devices shows what each device is and when it was last active.
- AI agents can join Lupyd as ordinary users: give an agent its own account and run the local MCP connector (`firefly-mcp`) on its machine. People message it or add it to their groups like anyone else.

### Fixed

- A direct message could fail to decrypt on the receiving device ("Bad Mac") when a new encryption key happened to reuse the number of one still in use.

### iOS

- Lupyd for iPhone and iPad is in public beta: join it on TestFlight at https://testflight.apple.com/join/2tfSzfTj.

### Web

- If part of the app fails to download while it loads, Lupyd tries again by itself, and if it still can't load, it says so and offers a Refresh button instead of staying on the loading screen.

## 1.1.5 (2026-11-07)

Groups that follow you to every device, Leave Group, and messages that are never lost to a group change.

### New

- Leave Group: leave from any of your devices and the group goes from all of them. A member who left can be added back.
- Groups reach all your devices: a group you create or join on one device shows up on the others, including ones that were offline or signed in later.
- Renaming a group shows the new name on every device of every member.
- Sign in with Apple.
- On phones, the emoji tray takes the keyboard's place, so the message box no longer jumps when you switch between them.

### Improved

- Chats scroll smoothly: sent and received messages glide fully into view instead of appearing half hidden and jumping.
- Group chats on phones open at the latest message.
- On desktop, hovering over a message no longer dims the whole screen.

### Fixed

- A group message sent at the same moment as a group change (a rename, a new channel, someone joining or leaving) could be lost for some members.
- Edits, deletes and reactions in direct messages now apply on every device of both people, not just the one they were made on.
- Group owners can delete a group from its settings page again.
- On a device whose clock runs behind, the newest messages could be missing from a chat.
- Adding someone back to a group right after they joined could fail on one of their devices.
- Signing up no longer gets stuck on "Username already taken" for the name you just claimed.

### Web

- In a private window, Lupyd now explains why it needs a normal one: it keeps your encrypted messages in the browser's storage, which Firefox turns off in private windows.

## 1.1.4 (2026-11-02)

Messages to contacts with an old, silent device go through, and long-lived groups keep working.

### Fixed

- Messages to a contact with a device that hadn't been used in over a month no longer stay stuck behind the clock icon.
- Group membership credentials renew before they expire, so groups more than a year old can still take new members.

### Web

- Notifications for new messages, in the page and from the browser.
- Private windows that can't store messages are detected up front instead of breaking after sign-in.
- Signing in with Google on Firefox no longer reloads the page.
- Coming back online after a failed refresh reconnects straight away.

## 1.1.3 (2026-10-30)

Stay signed in through server hiccups, wrong clocks and crashes.

### Fixed

- You stay signed in when the server briefly rejects a session, when your device's clock is wrong, or after the app crashes.
- Only a sign-in that has really ended (revoked or expired) signs you out; failed refreshes retry with a pause instead.

### Removed

- Single sign-on (SSO) sign-in.

## 1.1.2 (2026-10-29)

Lupyd on the web, presence, and sessions that stay alive.

### New

- Lupyd in the browser at app.lupyd.com, with the same encryption as the apps.
- Older direct messages load from your other devices, and group history loads as you scroll.
- Presence: see who is online and when they were last seen, or hide your own status. Group member lists show who's online.
- Log out of all devices from Settings; a removed device is signed out.
- Sign in with a link sent to your email.

### Fixed

- Phones no longer get signed out overnight.

## 1.1.1 (2026-10-12)

Offline mode, faster connections and message requests.

### New

- Offline mode: read your chats and groups without a network; messages you write offline go out once you're back.
- Message requests: messages from people you haven't accepted arrive as requests you can accept or decline.
- Discover: find people and start a conversation.

### Improved

- Faster, steadier connections (WebTransport first, WebSocket as a fallback).
- Your devices moved to the Account page and chat backup to the Privacy page.
- Calls and plan handling.

### Fixed

- A crash when showing notifications on Android.
- Keyboard layout in group channels on iPhone and iPad.

## 1.0.0 (2026-09-26)

The first stable release.

### New

- End-to-end encrypted direct messages (Signal Protocol) and groups with channels (MLS), on desktop and Android.
- Voice and video calls, group invites, photo and camera sharing, and group notifications.

### Fixed

- A network crash on Android.

## 0.0.21 – 0.1.3 (2026-07-04)

Public betas, July to September 2026.

### New

- Encrypted messaging and groups, message requests, group invites and calls.
- Photos converted to WebP before upload, camera capture in chats, and group notifications.
- The Linux AppImage.
