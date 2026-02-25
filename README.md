### Help would be appreciated for translating project to English
## Some code is proprietary and I can't edit it. Would appreciate help

<div align="center">
<h1>B1 memory management</h1>
<a href="http://cppmicroservices.org/"><img alt="C Language" src="https://img.shields.io/badge/-C-black?logo=c&style=flat-square&logoColor=ffffff"></a>
<a href="http://cppmicroservices.org/"><img alt="C++ Language" src="https://img.shields.io/badge/-C++-808080?logo=c%2B%2B&style=flat-square&logoColor=ffffff"></a>
<a href="https://www.python.org/"><img alt="Bash Shell" src="https://img.shields.io/badge/-Bash-ae9a5a?style=flat-square&logo=shell&logoColor=ffffff"></a>
<p>Third-party Android memory management, aimed to be less aggressive, for low RAM devices</p>
</div>

## What does it do?
- Managing the survival and termination of background processes
- Specifying the release of background application child processes
- Preventing Low Memory Killer Daemon from killing background processes
- Automatically releasing non-essential memory
- Putting applications to sleep to reduce CPU and memory usage

## 💡Description
- This module only supports Android 8 to 16 (only tested on 15), and arm64-v8a.
- Latest Magisk version should be used, and KernelSu is working.
- This module is not known to conflict with any others

### Default List Path
![列表图片](image/list.jpg)
- List File: /sdcard/Android/HChai/HC_memory/名单列表.conf

## 📱Terminal UI
Custom toggle functionality, only supports simple feature toggling. For more detailed parameter configurations, please see 📝 Custom Configuration.
![UI图片](image/ui_us.jpg)
How to access the Terminal UI interface?
- You can use the `amui` command in Termux or execute /sdcard/Android/HChai/HC_memory/`terminal.sh` in the mt manager.

How to save and toggle features?
- Use the arrow keys for navigation and press Enter to save.
- If there's no keyboard, click on the bottom right corner "lm" to summon the keyboard.

What does the feature do?
- An explanation will be added to the Terminal UI later. Currently, only the Json configuration guide is available.

## 📝Custom Configuration
The built-in configuration is suitable for most devices, but there are still some devices that may not work with the default configuration. Therefore, more adjustable parameters are provided. This requirement was already taken into consideration when designing the HAMv2 framework, and most parameters can be customized and adjusted. Moreover, this project can be embedded and run within other modules. The JSON configuration file is located at `/data/adb/modules/Hc_memory/config/memory.json`

### Project Information
```json
"project": {
    "name": "官方配置 [23.06.25]",
    "author": "火機@coolapk"
}
```

| Field  | Type   | Description                                  |
| ------ | ------ | -------------------------------------------- |
| name   | string | Name of the configuration file               |
| author | string | Author information of the configuration file |

The `name` and `author` are reflected in the logs in the following format:
```
[2023-07-06 19:00:22] [info] config 官方配置 [23.06.25] | by: 火機@coolapk
```

- For more detailed instructions on the JSON configuration file, please refer to[here.](config/JSON-CONFIG.md)

## 🔍Frequently Asked Questions

Can it be used in conjunction with other memory optimization modules?
- B1 memory management works completely differently from other memory optimization methods, so using it together with other modules will only yield a cumulative effect of 1+1=2.

Does it consume power?
- Not at all. A considerable amount of time optimizing the core code was spent while developing the HAMv2 framework. It is implemented in low-level languages such as C/C++, resulting in minimal power consumption that can be completely ignored.

Does it conflict with other Magisk modules or Xposed modules?
- It is highly unlikely to conflict with other modules. So far, no conflicts have been encountered with this module.

Does it cause power consumption during standby?
- The HAMv2 framework does not cause power consumption during standby, as the B1 memory management enters a sleep state when the device is in standby mode.

Why is the background process still killed even after enabling the lmkd process kill prevention?
- This is because it only prevents lmkd from killing background processes and does not include the background process killing programs from various phone manufacturers. MIUI/HyperOS are really aggressive with this.

How to configure the smart list?
- To configure the smart list, you need to add the rule "KILL package_name:subprocess_name" in the respective list. Before adding, make sure you understand the functionality and purpose of the subprocess to avoid any unexpected issues.

Why does the device enter fb mode after a certain period of time?
- Most cases of this issue occur on Samsung devices when the hook to prevent lmkd process killing is enabled. This is likely the cause of the problem. Currently, there is no solution available, but you can try disabling the hook to prevent lmkd process killing to resolve it.

Why is the process playing audio being paused?
- The occurrence of audio process being paused is rare. If it indeed happens, you can add the process to the whitelist or disable the app hibernation feature. This will ensure continuous operation of the audio process without being paused.

Not compatible with this platform: xxxx error when installing the module.
- Currently, the module only supports the arm-v8a platform and does not support other platforms.

## 🚀download
- [Go to Github to download](https://github.com/Referrance/B1Mem/releases)


## 🙏Acknowledgments

Thanks to the following users or projects for their source code contributions to this project:  
- [@yc9559](https://github.com/yc9559)
- [@HChenX](https://github.com/HChenX)

Thanks to the following users for their testing feedback and bug identification:
- @火機(coolapk)

Thanks to the really cool guy who originally made this:
- [@OneB1ank](https://github.com/OneB1ank)
