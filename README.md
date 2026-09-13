# HOP Launcher

Кроссплатформенный лаунчер Minecraft (офлайн и Microsoft-аккаунты, любые версии, моды, ресурс-паки, друзья).

Готового `.exe` в репозитории нет — лаунчер нужно собрать из исходников самому. Это делается один раз через PowerShell, дальше просто запускаешь готовый файл.

## Что нужно скачать перед запуском

1. **[Node.js](https://nodejs.org/)** — версия LTS (18 или новее). При установке отметь галочку "Add to PATH" (обычно стоит по умолчанию).
2. **[Rust](https://www.rust-lang.org/tools/install)** — скачай `rustup-init.exe` и запусти, в консоли просто нажми Enter на всех вопросах (установка по умолчанию).
3. **[Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)** — нужны Rust'у для компиляции на Windows. При установке выбери компонент **"Desktop development with C++"**.
4. **[WebView2 Runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)** — на большинстве Windows 10/11 уже установлен по умолчанию (входит в систему). Если лаунчер после сборки не открывает окно — установи по этой ссылке.
5. **[Java (Adoptium Temurin)](https://adoptium.net/temurin/releases/)** — нужна не для сборки лаунчера, а чтобы потом ЗАПУСКАТЬ саму игру Minecraft. Скачай версию **17** или новее.

## Как собрать и запустить (через PowerShell)

1. Скачай и распакуй этот репозиторий (кнопка **Code → Download ZIP** на GitHub, либо `git clone`).
2. Открой **PowerShell**.
3. Перейди в папку проекта, например:
   ```powershell
   cd C:\Users\ИМЯ\Downloads\vita-launcher
```

1. Установи зависимости проекта:
    
    ```powershell
    npm install
    ```
    
2. Собери готовый установщик:
    
    ```powershell
    npm run build
    ```
    
3. Подожди, пока сборка закончится (первый раз может занять несколько минут — Rust компилирует всё с нуля).
4. Готовый установщик появится здесь:
    
    ```
    src-tauri\target\release\bundle\nsis\HOP_0.1.0_x64-setup.exe
    ```
    
5. Запусти этот `.exe` — он установит HOP на компьютер, дальше лаунчер запускается как обычная программа, из меню Пуск или с ярлыка на рабочем столе.

## Быстрый запуск без установки (режим разработки)

Если не нужен установщик, а просто хочется быстро открыть лаунчер и проверить, что всё работает:

```powershell
npm run dev
```

Это откроет лаунчер сразу, без сборки полноценного `.exe`.

## Возможные проблемы

- **`npm` не найден** — значит Node.js не установился в PATH, переустанови Node.js и перезапусти PowerShell.
- **`cargo` не найден** — значит Rust не установился в PATH, переустанови Rust и перезапусти PowerShell.
- **Ошибка про `link.exe` или `MSVC`** — не установлены [Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) с компонентом C++, установи их.
- **Игра не запускается, ошибка про Java** — установи [Java 17+](https://adoptium.net/temurin/releases/) и перезапусти лаунчер.

```
