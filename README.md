# VoidEngine - Native Rust CPU Optimizer for Voices of the Void

**VoidEngine** is a low-level runtime CPU & memory-level optimizer built in **Rust** specifically for **Voices of the Void** (including **Multivoid** multiplayer co-op). 

Unlike fake config tweaks, DLSS/FSR blur, or frame generation, VoidEngine delivers **+70% to +150% pure native FPS** with **zero input lag** and **zero visual degradation** by eliminating Unreal Engine 4 single-threaded `GameThread` bottlenecks.

---

## How It Works Under the Hood (Architecture)

Voices of the Void suffers from severe CPU bottlenecks on cluttered bases (Day 20-40+) because hundreds of static/physics props, off-screen screens, and background AI actors constantly fire `ReceiveTick` events on a single CPU thread.

VoidEngine solves this directly in memory without modifying game `.pak` files or breaking save files:
* **VTable `ProcessEvent` Spatial Culling:** Dynamically throttles background tick rates for distant and out-of-FOV props while keeping critical observatory equipment (`analogDScreenTest`, radar, signal tape reels, servers, transformers, Kerfur-O, and story triggers/events) running at a strict 1:1 native rate.
* **Multithreaded Offloading:** Moves spatial math and distance evaluations off the UE4 `GameThread`.
* **Live In-Game Overlay (`[DELETE]`):** Real-time control panel with 1-click AI freeze toggles for **Roaches** and **Living Mannequins**, 4 instant render presets (`[Numpad 1–4]`), and clean native UE4 **TAAU** temporal upscaling (`[Numpad 5–7]`).

---

## Verified Community Benchmarks (v1.02)

| Hardware Configuration | Mode / Save State | Vanilla FPS | VoidEngine FPS |
| :--- | :--- | :---: | :---: |
| **Ryzen 7 5700X3D + RTX 4070** | Day 36 Cluttered Base | 135–150 FPS | **300–320+ FPS** |
| **Core i5-12450H + RTX 4050 (Laptop)** | Day 1 Observatory | 95–100 FPS | **190–200 FPS** |
| **Ryzen 5 5500 + RTX 5050** | Multivoid Co-op | 90–100 FPS | **190–200 FPS** |
| **Core i3-9100F + GTX 1650 (4C/4T)** | Base Interior | 50–60 FPS | **140–155 FPS** |
| **Core i7-4790 (DDR3) + GTX 1060 6GB** | Multivoid Co-op | 45–60 FPS | **100–115 FPS** |
| **Xeon E5-2640 v4 + RX 480 (Linux Proton)** | Base Interior | 30–40 FPS | **70 FPS (Locked)** |
| **Legacy 2-Core PC (2011)** | Intel Core i3-2120 (DDR3) + GTX 960 | ~30–40 FPS | **60–70 FPS (Base) / 80–90 (Forest)**


---

## Why Not Free Thunderstore Mods or `Engine.ini` Tweaks?

Players searching for Voices of the Void optimization often run into outdated guides or older Thunderstore packages. Here is how they compare to **VoidEngine** on modern versions (`0.9+ / 0.10+`):

| Alternative Solution | Works on `0.9+ / 0.10+`? | Why It Doesn't Fix Late-Game Base Lag |
| :--- | :---: | :--- |
| **`FoliageTweaks` / `QuickLoadMod`** | ❌ Outdated (`0.7 / 0.8`) | Built for legacy VoidMod versions. Only adjusted grass LODs or cached textures on disk - zero impact on the single-threaded `GameThread` actor tick bottleneck. |
| **`CleanBase` / Garbage Removers** | ⚠️ Destructive | Permanently deletes world clutter instead of optimizing it. Once you decorate your base on Day 20-40+ with hundreds of drives, plushies, lights, and items, severe CPU lag returns in full. |
| **`Engine.ini` / Lossless Scaling** | ⚠️ Visual / Input Penalty | Config files cannot stop UE4 Blueprints from firing `ReceiveTick`, while external Frame Generation (`LSFG`) smears dark UI elements and adds heavy mouse input latency at low base framerates. |
| **VoidEngine (Native Rust)** | ✅ **`0.9+ / 0.10+` & Multivoid** | **Non-destructive runtime CPU optimization.** Keeps 100% of your items, physics, and story events intact while doubling real native FPS with zero input lag. |

---

## Future Roadmap: Beyond Voices of the Void

**VoidEngine** is built on a modular, low-level **Rust + UE4SS** runtime architecture rather than hardcoded game-specific hacks. Because Unreal Engine 4 shares a unified `UObject` / `ProcessEvent` / `ReceiveTick` foundation across titles, our core spatial culling and multithreaded offloading engine is highly portable.

* **Short-Term Focus:** Polishing **VoidEngine** for *Voices of the Void* (`v1.1` Weather & Dish Optimizer, new hardware presets, and 100% compatibility with upcoming game updates).
* **Long-Term Vision:** Depending on community feedback and support, we plan to port the **VoidEngine Rust Core** to other CPU-heavy indie titles and co-op games built on Unreal Engine 4 that suffer from single-threaded `GameThread` bottlenecks.

---

## Security, Privacy & Antivirus Transparency

Because VoidEngine is a compiled native C-ABI Rust library (`votv_network_boost.dll`) loaded via `UE4SS / shimloader` with offline cryptographic license verification (`Ed25519`), we maintain full transparency regarding binary safety:

* **100% Offline Execution:** VoidEngine contains **zero networking code** (`WinInet`, sockets, or HTTP clients are completely absent). It never connects to the internet or transmits telemetry.
* **Non-Destructive:** Operates strictly in RAM during runtime. Removing the mod folder instantly restores vanilla behavior with zero risk to your save files.
* **Official VirusTotal Scan (v1.02):** [**View Official VirusTotal Report**](https://www.virustotal.com/gui/file/5c8e08a17fb881a14b5eadd719f6886c8a4ff528e900f6da89e5dff629c9f4bc?nocache=1) - **Clean** on Microsoft Defender, Kaspersky, Malwarebytes, ESET-NOD32, Bitdefender, and Avast (Note: 2-4 generic heuristic ML flags from obscure engines may appear solely due to standard Rust release stripping and offline Ed25519 signature protection).

---

## Get VoidEngine & Official Links

VoidEngine is available with **Lifetime Access** (one-time purchase, all future updates including `v1.1` Weather & Dish Optimizer included):

* **International (USD / EUR / PayPal / Cards):** [**Get on Hipolink**](https://hipolink.net/yupl0ve_meow)
* **RU / CIS (RUB / Cards / SBP):** [**Get on Boosty**](https://boosty.to/yupl0ve)
* **Official YouTube Showcase & Benchmarks:** [**@yupl0ve_meow**](https://www.youtube.com/@yupl0ve_meow)
* **Official Discord Community & Support (The Velvet Room):** [**Join Discord Server**](https://discord.gg/ssCxswc3jn)

---

## 🇷🇺 Описание (VoidEngine для Voices of the Void)

**VoidEngine** - низкоуровневый нативный оптимизатор процессора на языке **Rust** для игры **Voices of the Void** (поддерживает версии `0.9+ / 0.10+` и мультиплеерный кооп-мод **Multivoid**).

Мод увеличивает частоту кадров на **+70%...150% честных нативных FPS** без генерации кадров, мыла и задержки ввода за счёт разгрузки однопоточного `GameThread` движка Unreal Engine 4.

---

### Планы на будущее: универсальное Rust-ядро для UE4

**VoidEngine** построен на модульной архитектуре (**Rust + UE4SS**), а не на жёстких костылях под одну игру. Поскольку движок Unreal Engine 4 использует единую систему объектов и событий (`UObject` / `ProcessEvent` / `ReceiveTick`), наше многопоточное ядро легко адаптируется под другие проекты.

* **Ближайшая цель:** развитие **VoidEngine** для *Voices of the Void* (крупный патч `v1.1` с оптимизацией погоды и тарелок, а также оперативная поддержка всех будущих обновлений игры).
* **Амбициозная цель:** в зависимости от отклика и поддержки комьюнити - портирование ядра **VoidEngine** на другие требовательные к процессору инди- и кооп-игры на Unreal Engine 4.

### Ключевые возможности (v1.02):
* **Умная фильтрация тиков (`ProcessEvent`):** усыпляет фоновые расчёты сотен пропов и мусора за стенами, сохраняя 100% ванильную работу радара, пульта скачивания сигналов, катушек записи, серверов, трансформаторов, Керфуса и всех сюжетных событий.
* **Встроенный оверлей на клавишу `[DELETE]`:** заморозка ИИ тараканов и живых манекенов в 1 клик, 4 мгновенных пресета графики (`[Numpad 1–4]`) и чёткий темпоральный апскейлер **TAAU** (`[Numpad 5–7]`).
* **Полная безопасность:** работает строго офлайн в оперативной памяти, не трогает сохранения и проверен на [**VirusTotal**](https://www.virustotal.com/gui/file/5c8e08a17fb881a14b5eadd719f6886c8a4ff528e900f6da89e5dff629c9f4bc?nocache=1).
* **Поддержка Windows 10/11 и Linux (Steam Proton / Wine).**

### Официальные ссылки:
* **Скачать мод (РФ и СНГ):** [Boosty](https://boosty.to/yupl0ve)
* **Зарубежные карты:** [Hipolink](https://hipolink.net/yupl0ve_meow)
* **YouTube-канал с тестами:** [YouTube.com](https://www.youtube.com/@yupl0ve_meow)
* **Discord-сервер поддержки и отзывов:** [Присоединиться к Discord-серверу](https://discord.gg/ssCxswc3jn)

---

### Почему старые моды с Thunderstore и `Engine.ini` не спасают?

* **`FoliageTweaks` и `QuickLoadMod`:** заброшены более полутора лет назад (под старые патчи `0.7 / 0.8`) и несовместимы с актуальными версиями `0.9+ / 0.10`. Они лишь резали прорисовку травы или кэшировали текстуры, никак не разгружая основной поток процессора (`GameThread`).
* **`CleanBase` / удаление мусора:** вместо оптимизации движка физически удаляют объекты с карты. Как только к 20-30 дню вы сами обставите базу своими дисками, декором, едой и светом - просадки FPS вернутся в полном объёме. **VoidEngine** поднимает FPS в 2 раза, сохраняя каждый ваш предмет на месте.
* **Генераторы кадров (`Lossless Scaling`):** рисуют фейковые промежуточные кадры с артефактами в темноте и ощутимой задержкой мыши, тогда как **VoidEngine** даёт честный нативный отклик.

---
Created & maintained by **Inky** (`@yupl0ve_meow`)
