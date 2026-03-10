# NixBot - WhatsApp Bot

A powerful WhatsApp group management bot built with [Baileys](https://github.com/WhiskeySockets/Baileys) by **Aryan Rayhan**.

---

## Features

- Multi-device WhatsApp connection (QR Code / Pairing Code)
- Modular command system with 55+ commands
- Group management (kick, ban, antilink, welcome/leave messages)
- AI integration (Gemini, Baby AI chatbot)
- Media tools (YouTube download, image upscale, background removal, screenshot)
- Economy system (balance, daily rewards, slot game)
- Fun & games (quiz, flag guessing, emoji mix, pair)
- Role-based access control (User / Admin / Developer)
- Per-group settings (aliases, shortcuts, rules, welcome/leave)
- Auto-restart and memory optimization

---

## Setup

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure `config.json`

Edit `config.json` with your details:

```json
{
  "prefix": "!",
  "botName": "NixBot",
  "ownerNumber": ["your_number"],
  "loginMethod": "paircode",
  "apis": "https://api.nixhost.top",
  "database": {
    "type": "sqlite"
  }
}
```

### 3. Get Pairing Code

Visit the pairing code page to link your WhatsApp:

```
https://paircode-quwu.onrender.com/
```

Or set `"loginMethod": "paircode"` in `config.json` and the bot will generate a pairing code in the console using your owner number.

### 4. Start the Bot

```bash
node index.js
```

---

## Project Structure

```
NixBot/
â”œâ”€â”€ index.js               # Entry point - process supervisor
â”œâ”€â”€ main.js                # WhatsApp connection & auth handler
â”œâ”€â”€ main_handler.js        # Message router & command loader
â”œâ”€â”€ utils.js               # Global utilities & API config
â”œâ”€â”€ config.json            # Bot configuration
â”œâ”€â”€ bot/
â”‚   â””â”€â”€ push.js            # Command executor & alias resolver
â”œâ”€â”€ scripts/
â”‚   â”œâ”€â”€ cmds/              # Command modules (55+)
â”‚   â””â”€â”€ events/            # Event handlers (welcome, leave, logs)
â”œâ”€â”€ database/
â”‚   â”œâ”€â”€ manager.js         # Database layer (SQLite / MongoDB)
â”‚   â””â”€â”€ data/              # Data files (users, groups, bans)
â””â”€â”€ session/               # WhatsApp auth session
```

---

## Commands

### AI
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `gemini` | - | Google Gemini AI (text + image analysis) | Everyone |
| `baby` | `nix`, `bot`, `babu`, `beby` | AI Chatbot with teach/reply/edit/remove | Everyone |
| `prompt` | - | Extract AI prompt from image | Everyone |

### Media
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `video` | - | Download YouTube video by search or link | Everyone |
| `youtube` | `ytb` | YouTube audio/video download | Everyone |
| `sing` | - | Download music from YouTube | Everyone |
| `album` | - | Send media albums | Everyone |
| `alldl` | - | Universal media downloader | Everyone |

### Image
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `4k` | `upscale` | Upscale images to 4K resolution | Everyone |
| `mj` | `midjourney` | Generate AI images with Midjourney | Everyone |
| `removebg` | `rbg` | Remove background from image | Everyone |
| `imgbb` | - | Upload image to ImgBB | Everyone |
| `pp` | - | Get user profile picture | Everyone |

### Utility
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `ss` | `screenshot`, `snap`, `web` | Take website screenshot | Everyone |
| `say` | - | Text-to-speech voice message | Everyone |
| `translate` | `t`, `trans` | Translate text to any language | Everyone |
| `weather` | `wthr` | Current weather for any city | Everyone |
| `emojimix` | - | Mix two emojis together | Everyone |
| `ping` | - | Check bot response time | Everyone |
| `uptime` | - | Bot uptime info | Everyone |
| `rank` | - | User rank card or leaderboard | Everyone |
| `stats` | - | Most used commands chart | Everyone |
| `uid` | `u`, `id` | Get user ID | Everyone |
| `tid` | - | Get group/thread ID | Everyone |
| `busy` | - | Do not disturb mode | Everyone |
| `called` | - | Check who tagged you while away | Everyone |
| `unsend` | `un`, `uns` | Unsend a bot message | Everyone |

### Group Management
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `adduser` | `add` | Add user to group | Admin |
| `kick` | - | Kick member from group | Admin |
| `ban` | - | Ban user (auto-kick if re-added) | Admin |
| `tagall` | - | Tag all group members | Admin |
| `antilink` | - | Link blocking policies | Admin |
| `spamkick` | - | Auto kick spammers | Admin |
| `setwelcome` | - | Set custom welcome message | Admin |
| `setleave` | - | Set custom leave message | Admin |
| `rules` | - | Group rules management | Everyone |
| `setalias` | - | Custom command aliases per group | Admin |
| `shortcut` | - | Message shortcuts for group | Everyone |

### Game & Economy
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `flag` | - | Guess the country from its flag ($50 reward) | Everyone |
| `quiz` | - | Trivia quiz game | Everyone |
| `slot` | `slots` | Slot machine game | Everyone |
| `daily` | - | Daily coin reward | Everyone |
| `balance` | - | Check your balance | Everyone |
| `pair` | - | Pair with someone in the group | Everyone |

### Owner / Developer
| Command | Aliases | Description | Role |
|---------|---------|-------------|------|
| `admin` | - | Manage admins | Owner |
| `cmd` | - | Enable/disable commands | Owner |
| `setrole` | - | Set user roles | Owner |
| `loadconfig` | `loadcf` | Reload bot config | Owner |
| `notification` | `notify`, `noti` | Send notification to all groups | Owner |
| `user` | - | Manage users in bot system | Owner |
| `delete` | `d` | Delete cache/temp or command files | Owner |
| `out` | - | Bot leaves the group | Owner |
| `prefix` | - | Change bot prefix | Everyone |
| `adboxonly` | - | Admin-only box mode | Owner |
| `restart` | - | Restart the bot | Developer |
| `eval` | - | Execute code | Developer |
| `shell` | `sh`, `terminal` | Execute shell commands | Developer |
| `update` | `upgrade` | Update bot | Developer |

---

## Events

| Event | Description |
|-------|-------------|
| `welcome.js` | Sends welcome message when a member joins |
| `leave.js` | Sends leave/remove message when a member leaves |
| `logsbot.js` | Logs group add/kick events to admin inbox |

---

## Role System

| Role | Level | Access |
|------|-------|--------|
| User | 0 | Basic commands |
| Admin | 1-2 | Group management commands |
| Developer | 3 | Full access (eval, shell, restart) |

---

## Command Module Structure

Each command is a `.js` file inside `scripts/cmds/` exporting:

```js
module.exports = {
    config: {
        name: "example",
        aliases: ["ex"],
        version: "0.0.1",
        role: 0,
        author: "ArYAN",
        countDown: 5,
        description: "Example command",
        category: "utility",
        guide: {
            en: "{pn} <argument>"
        }
    },

    onStart: async function ({ sock, chatId, event, args, reply, prefix }) {
        reply("Hello from NixBot!");
    }
};
```

### Available Parameters in `onStart`

| Parameter | Description |
|-----------|-------------|
| `sock` | WhatsApp socket connection |
| `chatId` | Current chat/group ID |
| `event` | Raw message event object |
| `args` | Command arguments array |
| `reply` | Quick reply function |
| `prefix` | Current bot prefix |
| `senderNumber` | Sender's phone number |
| `isGroup` | Whether message is from a group |
| `isAdmin` | Whether sender is group admin |
| `isBotAdmin` | Whether bot is group admin |

---

## Global API System

All API endpoints and keys are centralized in `config.json` and loaded into:

- `global.NixBot.apis` â€” API base URLs (base, flag, baby, nixConfig, weather, tenor, imgbb)
- `global.NixBot.keys` â€” API keys (weather, imgbb, tenor)

Commands only reference `global.NixBot.apis.*` and `global.NixBot.keys.*`. No hardcoded URLs or keys in any command file.

---

## Database

Supports two backends (configured in `config.json`):

- **SQLite** (default) â€” saves to `database/data/data.sqlite`
- **MongoDB** â€” requires `database.mongoURI` in config

### Data APIs
- `usersData` â€” get/set/getAll/delete user data (balance, name, exp, level)
- `threadsData` â€” get/set/getAll/delete group data (welcome, leave, bans, aliases)

---

## Pairing Code

To connect the bot to WhatsApp:

1. **Web Method**: Go to [https://paircode-quwu.onrender.com/](https://paircode-quwu.onrender.com/) and follow the instructions to get your pairing code
2. **Console Method**: Set `"loginMethod": "paircode"` in `config.json`, start the bot, and enter the pairing code shown in the console into WhatsApp (Settings > Linked Devices > Link a Device)

---

## Memory & Performance

- Forced garbage collection every 60 seconds
- RAM monitoring with auto-restart at 400MB threshold
- Lightweight store for session data
- Cache auto-cleanup after media commands

---

## Credits

- **Developer**: Aryan Rayhan
- **Version**: 0.0.1
- **Library**: [@whiskeysockets/baileys](https://github.com/WhiskeySockets/Baileys)
- **Facebook**: [fb.com/100001611578438](https://fb.com/100001611578438)
- **Telegram**: [t.me/@aryannix](https://t.me/@aryannix)
- **WhatsApp**: [wa.me/+8801903910486](https://wa.me/+8801903910486)
- **Instagram**: [ig.com/aryan_rayhan_07](https://ig.com/aryan_rayhan_07)
