# GShow

A comprehensive Minecraft plugin that allows players to **share their inventory, ender chest, money, item-in-hand, and ping** information in chat with interactive **hover and click** functionality.

---

## ✨ Features

- **Interactive Chat Display**  
  Players can type `[inv]`, `[enderchest]`, `[money]`, `[item]`, or `[ping]` in chat to share their data.

- **Hover & Click Support**  
  Messages are interactive—hover for tooltips, click to view detailed GUI/info.

- **Live Inventory Updates** *(Configurable)*  
  Inventory and ender chest views update in real time if enabled.

- **30-Second Timeout**  
  Shared data automatically expires after 30 seconds for privacy and security.

- **Fully Configurable**  
  Supports color codes, custom regex patterns, and message formatting.

- **Economy Integration**  
  Works with any Vault-compatible economy plugin.

- **Permission System**  
  Fine-grained permission control for each feature.

- **View-Only Access**  
  Players can view shared inventories but cannot modify them.

---

## 📦 Installation

1. Download the plugin `.jar` file.
2. Place it into your server’s `/plugins` folder.
3. Restart your server.
4. Configure the plugin via `/plugins/GShow/config.yml`.

---

## ⚙️ Dependencies

- **Required:**  
  - [Spigot](https://www.spigotmc.org/) or [Paper](https://papermc.io/) `1.16+`  
  - [Vault](https://www.spigotmc.org/resources/vault.34315/)

- **Optional:**  
  - [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) (for advanced placeholders)

---

## 🛠 Configuration

<details>
<summary><strong>Click to view <code>config.yml</code></strong></summary>

```yaml
# GShow Plugin Configuration
# Color codes: &0-&9, &a-&f, &k-&o, &r

# Regex patterns for detecting show commands in chat
# To disable a feature simply remove the list and add [] after the feature
# Example: inventory: []
# Example: enderchest: []
# Example: money: []
# Example: ping: []
# Example: item: []

patterns:
  inventory:
    - "\\[inv\\]"
    - "\\[inventory\\]"
    - "\\[items\\]"
  enderchest:
    - "\\[enderchest\\]"
    - "\\[ender\\]"
    - "\\[ec\\]"
  money:
    - "\\[money\\]"
    - "\\[balance\\]"
    - "\\[bal\\]"
  ping:
    - "\\[ping\\]"
    - "\\[ms\\]"
    - "\\[latency\\]"
  item:
    - "\\[item\\]"
    - "\\[hand\\]"
    - "\\[i\\]"

# Chat output messages (supports color codes, hex and placeholders if PlaceholderAPI is installed)
messages:
  global:
    no_permission: "&cYou don't have permission to use this command!"
    reload_success: "&aGShow configuration reloaded successfully!"
  inventory:
    format: "&e&lGSHOW &8/ &f{player} &7is showing their &bInventory"
    hover: "&eClick to view {player}'s inventory"
    no_permission: "&cYou don't have permission to view inventories!"
    expired: "&cThis inventory view has expired!"
  enderchest:
    format: "&e&lGSHOW &8/ &f{player} &7is showing their &dEnder Chest"
    hover: "&eClick to view {player}'s ender chest"
    no_permission: "&cYou don't have permission to view ender chests!"
    expired: "&cThis ender chest view has expired!"
  money:
    format: "&e&lGSHOW &8/ &f{player} &7has &a{amount}"
    hover: "&eShows {player}'s balance"
    no_permission: "&cYou don't have permission to view balances!"
    expired: "&cThis balance view has expired!"
  ping:
    format: "&e&lGSHOW &8/ &f{player} &7has &e{ping}ms &7ping"
    hover: "&eShows {player}'s connection ping"
    no_permission: "&cYou don't have permission to view ping!"
    expired: "&cThis ping view has expired!"
  item:
    format_1x: "&e&lGSHOW &8/ &f{player} &7is showing &b{item}" # If the amount of item in hand is 1
    format: "&e&lGSHOW &8/ &f{player} &7is showing &e{amount}x &b{item}" #  If the amount of item in hand is more than 1
    hover: "&eClick to view {player}'s {item}"
    no_item_in_hand: "&cYou must be holding an item to show it!"
    no_permission: "&cYou don't have permission to view items!"
    expired: "&cThis item view has expired!"
  shulker:
    format: "&e&lGSHOW &8/ &f{player} &7is showing &b{item}"
    hover: "&eClick to view {player}'s shulker box"
    no_permission: "&cYou don't have permission to view shulker boxes!"
    expired: "&cThis shulker box view has expired!"

# Settings
settings:
  view_timeout: 30  # in seconds
  enable_live_updates: true # Whether to enable live updates for views
  require_permission: false # Whether to require permissions for "viewing"

# Permissions for commands and features
permissions:
  use: "gshow.use"
  admin: "gshow.admin"
  view:
    inventory: "gshow.view.inventory"
    enderchest: "gshow.view.enderchest"
    money: "gshow.view.money"
    ping: "gshow.view.ping"
    item: "gshow.view.item"
    shulker: "gshow.view.shulker"

config-version: 1 # Do not change this value
```

</details>

---

## 🔧 Commands

| Command           | Description                         | Permission      |
|------------------|-------------------------------------|-----------------|
| `/gshow reload`  | Reloads the plugin configuration     | `gshow.admin`   |

---

## 🔐 Permissions

| Permission                   | Description                                  |
|-----------------------------|----------------------------------------------|
| `gshow.admin`               | Access to admin commands                     |
| `gshow.use`                 | Use the show features in chat                |
| `gshow.view.inventory`      | View shared inventories                      |
| `gshow.view.enderchest`     | View shared ender chests                     |
| `gshow.view.money`          | View shared money information                |
| `gshow.view.ping`           | View shared ping information                 |
| `gshow.view.item`           | View shared items shown in chat              |
| `gshow.view.shulker`        | View shared shulker shown in chat            |

---

## 💬 Usage

1. Type a pattern like `[inv]`, `[enderchest]`, `[money]`, `[item]`, or `[ping]` in chat.
2. Other players will see an interactive message.
3. Clicking inventory/ender chest shows a **read-only GUI**.
4. Clicking money or ping shows the value in chat.
5. All shared information expires after **30 seconds**.

---

## 🔒 Security Features

- ⏳ **Timeout:** Shared information auto-expires after 30 seconds.  
- 🔐 **Permission Checks:** Configurable permissions for all features.  
- 👁️ **View-Only Access:** No one can modify shared inventories.  
- 🧼 **No Storage:** No persistent data is saved to disk.

---

## 🤝 Support

For issues, suggestions, or contributions:
- 📬 Open an [issue](../../issues)
- 💬 Contact me via [Discord](https://discordapp.com/users/709208284489449604)
- ⭐ Star the project if you find it useful!
