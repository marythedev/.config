# Environment Configurations

Терминал
---
![image](https://github.com/marythedev/.config/assets/79389256/21817e92-9b7c-4360-b027-69ee160c5bba)
1. Установка [Chocolatey](https://chocolatey.org/install) - в Powershell выполняем команду (от администратора)
    ```
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```

2. Установка [Starship](https://github.com/starship/starship/blob/master/docs/ru-RU/guide/README.md)
    ```
    choco install starship
    ```

3. Настройка Powershell для автоматического запуска Starship
   1. Открываем файл `Microsoft.PowerShell_profile.ps1` в VSCode
      ```
      code $profile
      ```
   2. В файл пишем и сохраняем
      ```
      Invoke-Expression (&starship init powershell)
      ```
   3. Если выпадет [ошибка "выполнение сценариев отключено в этой системе"](https://ru.stackoverflow.com/questions/935212/powershell-выполнение-сценариев-отключено-в-этой-системе), в Powershell (от администратора) выполняем команду 
      ```
      Set-ExecutionPolicy RemoteSigned
      ```

4. Настройка Starship
   1. [Создаем starship.toml](https://dev.to/ganmahmud/take-your-windows-powershell-to-the-next-level-by-starship-2gb2)
      ```
      New-Item -ItemType Directory -Force ~/.config;New-Item -ItemType file ~/.config/starship.toml;
      ```
   2. В созданный файл добавляем конфигурации из файла [starship.toml из этой репозитории](starship.toml).<br>
       Ссылки на иные конфигурационные опции:
       - https://starship.rs/config/
       - https://starship.rs/presets/
  3. Если терминал [не показывает эмодзи/иконки](https://starship.rs/faq/#why-don-t-i-see-a-glyph-symbol-in-my-prompt), скорее всего нужно установить/указать правильный шрифт "Nerd Font"
     1. Устанавливаем шрифт (команды для некоторых шрифтов, которые использую я)
        - ComicShannsMono Nerd Font
           ```
           choco install nerd-fonts-comicshannsmono
           ```
        - Inconsolata LGC Nerd Font (отображает также текст на кириллице)
           ```
           choco install nerd-fonts-inconsolatalgc
           ```
        - Monofur Nerd Font
           ```
           choco install nerd-fonts-monofur
           ```
        - Остальные возможные шрифты можно найти [здесь](https://github.com/ryanoasis/nerd-fonts/#option-7-unofficial-chocolatey-or-scoop-repositories).

     2. Открываем setting.json (в VSCode: `View` -> `Command Palette` -> `>Preferences: Open User Settings (JSON)`) и указываем шрифт
          ```
          "terminal.integrated.fontFamily": "Monofur Nerd Font"
          ```
          Если шрифт не отображается, то скорее всего нужно добавить "Mono", как в [случае с Hack - не "Hack Nerd Font", а "Hack Nerd Font Mono"](https://github.com/microsoft/vscode/issues/81497).
