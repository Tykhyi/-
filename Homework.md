# Самостійна робота
**Виконав студент групи РПЗ-33 Тихий Андрій**

## Порівняльна характеристика операційних систем (Windows та Android)

Для порівняння обрано ОС Windows 11 та мобільну ОС Android із фірмовою оболонкою One UI (Samsung Galaxy S24 Ultra).

| Критерій порівняння | Windows 11 (ПК / Ноутбук) | Android (Samsung Galaxy S24 Ultra) |
| :--- | :--- | :--- |
| **OS kernel architecture** | Combines features of a monolithic kernel and a microkernel. Core system services and drivers run in kernel space for maximum speed, but the architecture allows third-party drivers to be loaded as modules. | All basic services (memory, processor, drivers) run in a single kernel space. It has deep modifications for mobile devices, including aggressive power management (Wakelocks) and memory management (OOM Killer). |
| **User interface** | Optimized for precise mouse and keyboard control. Main elements: desktop, taskbar, Start menu. Also has powerful built-in command line interfaces (CLI) — PowerShell and Command Prompt. | Optimized for finger and gesture control. In the case of Samsung, the One UI shell is used on top of the base Android. Access to the CLI (terminal) is hidden by default for the average user. |
| **System Calls** | Applications do not access the kernel directly. They call API functions that generate software interrupts (in x64 architecture, the `syscall` instruction is used) via the System Service Dispatch Table (SSDT) to switch to kernel mode. | Classic Linux system calls are used. However, applications usually do not call them directly, but through the Android Framework (Java API). Instead of the standard `glibc` library, the `Bionic` library optimized for mobile devices is used (via the `svc` instruction on ARM processors). |

**1. Операційна система ПК (Windows 11)**
*Інтерфейс користувача (GUI) та інформація про систему:*
![Інтерфейс Windows 11](win_ui.png)
![Відомості про систему Windows](win_kernel.png)

**2. Мобільна операційна система (Android / One UI)**
*Сенсорний інтерфейс користувача та інформація про версію ядра:*
![Інтерфейс Android](android_ui.png)
![Відомості про ядро Android](android_kernel.png)
