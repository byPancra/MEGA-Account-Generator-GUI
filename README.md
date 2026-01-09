<div align="center">

**English** | [Português (Brasil)](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-pt-BR) | [Español](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-es) | [日本語](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-ja) | [繁體中文](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-zh-TW) | [简体中文](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-zh-CN)

</div>
<br>

<div align="center">

</div>

<div align="center">

  ![Mega Account Generator GUI](./img/readme-icon.png)

  <h1 align="center">Mega Account Generator GUI</h1>
  
  **The ultimate tool for automating MEGA.nz account creation and management.**
  
  *Generate, Manage, Tag, and Export your accounts with a professional-grade interface.*

  [![Python Version](https://img.shields.io/badge/python-3.8%2B-blue?style=for-the-badge&logo=python)](https://www.python.org/)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](./LICENSE)
  [![Status](https://img.shields.io/badge/status-active-success?style=for-the-badge)]()
  [![Releases](https://img.shields.io/github/downloads/byPancra/Mega-Account-Generator-GUI/total?style=for-the-badge&color=orange)](https://github.com/byPancra/Mega-Account-Generator-GUI/releases)

  [Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Advanced Management](#-advanced-management) • [FAQ](#-faq)

</div>

---

## 📋 Overview

**Mega Account Generator GUI** is a robust, desktop-grade application designed for power users who need to generate and manage [MEGA.nz](https://mega.nz) accounts in bulk. Unlike simple scripts, this tool provides a complete ecosystem for account lifecycle management, including tagging, filtering, status tracking, and data export.

Built with **Modern Python** (CustomTkinter) and **Thread-Safe Architecture**, it ensures reliability even when processing hundreds of accounts.

![Demo](./img/intro2.gif)

---

## :zap: Features

### 🚀 Core Generation
*   **High-Speed Multi-Threading**: Generate up to 8 accounts simultaneously.
*   **Smart Rate Limiting**: Intelligent delays and retry logic (up to 12 attempts) to bypass Mail.tm restrictions.
*   **Bundled Dependencies**: The executable version comes with `megatools` pre-packaged—no external setup required.

### 🛠️ Advanced Management
*   **Tagging System**: Organize accounts with custom tags (e.g., `Personal`, `Backup`, `Client-A`) for easy retrieval.
*   **Search & Filter**: Instantly find accounts by Email, Status (`Active`, `Disabled`, `Failed`), or Tags.
*   **Bulk Operations**:
    *   **Keep-Alive**: Automated sign-in to prevent account deletion due to inactivity.
    *   **Storage Check**: Auto-update used/free storage quotas for all accounts.
    *   **Account Control**: Disable specific accounts to exclude them from bulk operations (e.g., Keep-Alive checks) without deleting them.

### 💾 Data Freedom
*   **Professional Export**: Export your database to **Excel (.xlsx)** with formatted styling or **JSON** for programmatic use.
*   **Seamless Import**: Migrate data from other tools or backups via JSON/Excel import.
*   **Clipboard Integration**: One-click copy for emails and passwords.

### 🔒 Security & Reliability
*   **Thread-Safe CSV**: Prevents data corruption during concurrent writes.
*   **Crash Recovery**: "Stop" button gracefully halts operations, preserving data integrity.

---

## :rocket: Installation

### Option A: Standalone Executable (Recommended)
Download the latest release. No Python or external tools needed.
1.  Download `MegaGenerator.exe` from [Releases](https://github.com/byPancra/Mega-Account-Generator-GUI/releases).
2.  Run the executable.

### Option B: Running from Source

**Prerequisites:**
*   Python 3.8+
*   [Megatools](https://megatools.megous.com/) (Added to PATH)

**Steps:**
1.  **Clone the repository:**
    ```bash
    git clone https://github.com/byPancra/Mega-Account-Generator-GUI.git
    cd Mega-Account-Generator-GUI
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the application:**
    ```bash
    python gui.py
    ```

---

## :computer: Usage

### Generating Accounts
1.  Navigate to the **Generator** tab.
2.  Set the number of **Threads** and **Accounts** to generate.
3.  Click **"Generate Accounts"**.
4.  Credentials will be saved in `accounts.csv` and visible in the **Stored Accounts** tab.

### Managing Accounts
Navigate to the **Stored Accounts** tab:
*   **Search**: Type an email to filter instantly.
*   **Filter**: Use the dropdown to see only `Active`, `Disabled`, or `Failed` accounts.
*   **Edit**: Click the "Edit" button to change a saved password or manage Tags.
*   **Copy**: Quick buttons to copy credentials to clipboard.

### 💻 CLI Usage (Command Line)
For advanced users who prefer the terminal or want to integrate this into scripts.

```bash
# Basic usage (Generates 3 accounts)
python generate_accounts.py

# Generate 50 accounts with 5 threads
python generate_accounts.py -n 50 -t 5

# Set a specific password for all accounts
python generate_accounts.py -n 10 -p "MySecretPass123!"
```

**Arguments:**
*   `-n`, `--number`: Number of accounts to create (Default: 3)
*   `-t`, `--threads`: Number of concurrent threads (1-8)
*   `-p`, `--password`: Common password for all accounts (Optional)

#### Keep-Alive Check (Login & Storage)
To verify all accounts in `accounts.csv`, check their storage quota, and keep them active:

```bash
python signin_accounts.py
```

*   **No arguments required.**
*   Iterates through all accounts in `accounts.csv`.
*   **Skips accounts marked as "Disabled".**
*   Updates status to `Active` or `Login Failed`.
*   Updates used/free storage values.


---

## :briefcase: Advanced Management

### Exporting Data
You can export your entire account database for backup or external use.
1.  Click **Export** in the top right.
2.  Select **Excel** for a formatted spreadsheet or **JSON** for raw data.
3.  Choose a save location.

*Excel exports include color-coded status columns and formatted headers for easy reading.*

### Importing Data
Migrate from previous versions or other tools.
1.  Click **Import**.
2.  Select a valid `.json` or `.xlsx` file.
3.  The tool will merge the data into your `accounts.csv`.

---

## :grey_question: FAQ

<details>
<summary><strong>Why am I limited to 8 threads?</strong></summary>
The temporary email provider (Mail.tm) has strict rate limits. Exceeding 8 concurrent threads significantly increases the chance of IP bans or failed generations.
</details>

<details>
<summary><strong>What does the "Sign In" button do?</strong></summary>
It performs a "Keep-Alive" check. It attempts to log in to your accounts using `megatools`. This updates the storage quota information and signals to MEGA that the account is active, preventing deletion.
</details>

<details>
<summary><strong>Where are my accounts saved?</strong></summary>
All data is stored locally in `accounts.csv` in the application directory. You can also export this data using the Export feature.
</details>

<details>
<summary><strong>I see "Megatools not found" error.</strong></summary>
If running from source, ensure `megatools` is installed and added to your System PATH. If using the executable, this is handled automatically.
</details>

---

## :warning: Disclaimer

This tool is created for **educational and testing purposes only**. Using this software to abuse third-party services, bypass restrictions, or violate terms of service (ToS) of MEGA.nz or Mail.tm is strictly prohibited. The developer assumes no responsibility for misuse.

---

## :sparkling_heart: Acknowledgements

*   Based on the original work by [f-o/MEGA-Account-Generator](https://github.com/f-o/MEGA-Account-Generator).
*   GUI Components by [TomSchimansky/CustomTkinter](https://github.com/TomSchimansky/CustomTkinter).
*   Enhanced and Maintained by [byPancra](https://github.com/byPancra).

---

## :copyright: License

Distributed under the **MIT License**. See [LICENSE](LICENSE)  for details.

<div align="center">
  <sub>Developed with ❤️ by <a href="https://github.com/byPancra">byPancra</a></sub>
</div>
