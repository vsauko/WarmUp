## 🚀 TelegramPro

## 📱 Powerful tool for working with Telegram sessions

- 🐍 TelegramPro works primarily with Pyrogram sessions. All operations, including account warmup, are performed using Pyrogram.
- 🔄 When converting from Telethon or tdata formats, the result is always a Pyrogram session.
- 📊 The script automatically generates device parameters for each session, simulating different phone models and OS versions.
- 🔐 Implemented a system of gradual updating of session parameters to minimize detection risks.
- 📡 Supported operation via proxy to improve security and bypass possible restrictions.
- 📝 Operation results are saved to `results.json` file for further analysis.
- 🔧 The script includes error and retry handling mechanisms to improve reliability.


### Our tool provides a wide range of features including:

- ✨ Registration of new sessions
- 🔥 Warming up existing accounts
- 🧹 Checking and clearing inactive sessions
- 🔄 Conversion of sessions from different formats

## 🔧 Key features and mechanisms

- `warm_up_account`: The main function for warming up an account. Performs various actions including setting bios, avatar, subscribing to channels.
- `convert_sessions`: Provides conversion of sessions from Telethon and tdata formats to Pyrogram.
- `register_sessions`: Allows new sessions to be registered on the system.
- `check_and_remove_dead_sessions`: Checks the validity of sessions and removes inactive ones.

## 🚦 Artificial limits

- A global semaphore `GLOBAL_SEMAPHORE` is used to limit the number of concurrent sessions.
- A separate semaphore is created for each proxy to control the load on each proxy.

## 🔍 Detailed description of key functions

### 🔄 Session Conversion

Result:
- For tdata: new Pyrogram sessions in the tdata_path/[folder_name]/pyrogram_session.session folder
- For Telethon: new Pyrogram sessions in the folder sessions/[session_name]_pyrogram.session

### 📝 Register sessions

Result: 
- New .session file in the sessions/[session_name].session directory
- Add proxy to proxies.txt (if specified)

### ✅ Validity check

Result:
- Remove invalid sessions from the sessions/ directory
- Updated list of active sessions

### 🔥 Account warmup

Result:
- Updated account with new parameters (bio, avatar, username, 2FA, subscriptions)
- Recording the results of operations to the file results.json

### System Requirements:
- 🐍 Python version 3.10 or 3.11
- 🛠 Installed wheel package
- 📚 Dependencies from requirements.txt file

#### Installation Steps:

### Make sure you have the correct version of Python installed

### Install wheel:

```bash
pip install wheel
```

## Install dependencies:

```bash
pip install -r requirements.txt
```

## ⚙️ Customize the script

In the `main.py` file you will find a settings section where you can set:

- 🔑 API_ID and API_HASH
- 📁 Paths to directories (sessions, avatars, tdata, Telethon sessions)
- 🌐 Language parameters and number of concurrent sessions
- 📢 List of channels for subscription
- 🔒 Settings for two-factor authentication
- 🖼 Flags to set bio, avatar and random username

## 📂 Project structure

- 📁 `sessions`: Session files
- 📁 `avatar`: Avatar files
- 📁 `tdata_path`: tdata files for conversion
- 📁 `telethon_sessions`: Telethon sessions for conversion

## 🌐 Proxy configuration

Specify the proxy in the `proxies.txt` file in the format:

```
protocol://username:password@ip:port
```

For example: ``socks5://user:pass@1.2.3.4:1080``

## 🚀 Running the script

Run the script with the command:

```bash
python main.py
```

Follow the instructions in the console to select the desired operation.

## 🔄 Session conversion

TelegramPro supports converting sessions from Telethon and tdata formats to Pyrogram format. Here are the detailed instructions:

### 📁 Prepare files:

1. For tdata:
   - Place folders containing tdata files in the directory specified in `TDATA_PATH` (default is “tdata_path”)
   - Each folder must contain tdata files for one account

2. For Telethon:
  When converting sessions from Telethon format, it is recommended to use them paired with the corresponding .json files. This greatly improves the accuracy and efficiency of the conversion:

   - The .json file contains important metadata such as user_id, username, registration and last validation dates. This allows to recreate session parameters in Pyrogram format more accurately and consequently increases the chances of successful validation of the converted Telegram session by the Telegram server.

  Make sure the .json file is in the same directory as the .session file and has the same base name. For example, for a “session.session” session, there should be a “session.json” file.

### 🚀 Conversion process:

1. Run the script: `python main.py`.
2. Select the “Convert sessions” option
3. Specify the conversion type: tdata or Telethon

### 📤 result

- For tdata: 
  - New Pyrogram sessions will be created in the same folder where the tdata files are located
  - File name: `pyrogram_session.session`.

- For Telethon:
  - New Pyrogram sessions will be created in the `SESSIONS_DIR` directory (default “sessions”)
  - File name: `[original_name]_pyrogram.session`

### ✅ Verification:

After conversion, each session is automatically checked for validity. The results of the verification will be output to the console.


## ⚠️ Important notes and recommendations

- ✅ Make sure all required dependencies are present before running the script
- 🛡 Use proxies to increase security and minimize blocking risks
- 🔒 Use caution when working with a large number of accounts
- 📁 Check for correct file locations when converting sessions
- 🔐 Make sure you have read and write permissions on the specified directories
- 💾 Do not delete original files before successful conversion and session verification
- 🌐 When using proxies, make sure they are correctly specified in the `proxies.txt` file
- 🕒 Avoid too frequent requests to Telegram API to avoid time constraints
- 📜 Follow Telegram usage rules and local laws
- 🔄 Regularly update the script for new features and fixes
- 📊 Monitor your account usage statistics to detect anomalies
- 🆘 If you encounter any problems, please refer to the documentation or contact the developer community.


TelegramPro is a tool for legal management of Telegram accounts. Use it responsibly and in accordance with Telegram's terms of use.
