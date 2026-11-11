
# GERBER_X3
**Version 0.9.7.5**

Программа для подготовки G-кода из файлов Gerber (RS-274X) для фрезеровки печатных плат на станках с ЧПУ.

Программа поддерживает просмотр и редактирование Gerber-файлов, создание G-кода, поддержку файлов DXF.

Продукт разработан на основе GGeasy **XRay3D (Damir Bakyiev)**.

Исходный код отредактирован и адаптирован для работы со **схемАтор & платФорм** (Редактор **Theossr (Fyodor Abramov)**).

Другие версии программы и готовые сборки: [Releases](https://github.com/XRay3D/GERBER_X3/releases).

---

## Сборка из исходного кода (Windows)

Для сборки используется **MSYS2 UCRT64**, CMake и Ninja.

### 1. Установка MSYS2

1. Установите MSYS2.
2. Запустите терминал **MSYS2 UCRT64**.
3. Обновите пакеты:

```bash
pacman -Syu
```

Если терминал попросит закрыть его, закройте окно, снова запустите MSYS2 UCRT64 и выполните:

```bash
pacman -Su
```

### 2. Установка необходимых инструментов

Выполните команду:

```bash
pacman -S --needed \
  base-devel \
  git \
  mingw-w64-ucrt-x86_64-toolchain \
  mingw-w64-ucrt-x86_64-cmake \
  mingw-w64-ucrt-x86_64-ninja \
  mingw-w64-ucrt-x86_64-qt6-base \
  mingw-w64-ucrt-x86_64-qt6-declarative \
  mingw-w64-ucrt-x86_64-qt6-tools
```

### 3. Используемые версии

Проверенная конфигурация сборки:

| Инструмент | Версия |
|---|---|
| GCC / G++ | 16.2.0 |
| GNU Binutils (windres) | 2.47.20260726 |
| CMake | 4.4.4 |
| Qt | 6.11.2 |
| Ninja | 1.13.2 |

Проверить установленные версии можно командами:

```bash
g++ --version
windres --version
cmake --version
qmake6 --version
ninja --version
```

### 4. Сборка проекта

Перейдите в корневую папку проекта, создайте конфигурацию сборки:

```bash
cmake -S . -B build -G Ninja \
  -DCMAKE_BUILD_TYPE=Release \
  -DGERBER_NATIVE_MARCH=OFF \
  -DCMAKE_RC_FLAGS="--use-temp-file"
```

Параметр `--use-temp-file` необходим для корректной обработки Windows resource-файлов (`.rc`) с помощью GNU windres.

Запустите сборку:

```bash
cmake --build build --parallel 12
```

После успешной сборки исполняемый файл находится в:

```text
bin/Qt6._GNU_Release_x64/bin/GGEasy.exe
```

### Примечания

- Для сборки необходимо использовать именно терминал **MSYS2 UCRT64**.
- Перед повторной сборкой закройте запущенную программу `GGEasy.exe`, иначе Windows может запретить перезапись используемых DLL-файлов.
- При ошибке `Permission denied` во время создания DLL проверьте, не используется ли соответствующий файл другим процессом.

---

# GERBER_X3

**Version 0.9.7.5**

An application for generating G-code from Gerber (RS-274X) files for CNC milling of printed circuit boards.

The application supports viewing and editing Gerber files, G-code generation, and DXF file support.

The product is based on GGeasy, originally developed by **XRay3D (Damir Bakyiev)**.

The source code has been modified and adapted for use with **schemAtor & platForm** (Adaptation editor: **Theossr (Fyodor Abramov)**).

Other versions of the application and prebuilt releases: [Releases](https://github.com/XRay3D/GERBER_X3/releases).

---

## Building from source (Windows)

The project is built using **MSYS2 UCRT64**, CMake and Ninja.

### 1. Installing MSYS2

1. Install MSYS2.
2. Launch the **MSYS2 UCRT64** terminal.
3. Update the packages:

```bash
pacman -Syu
```

If the terminal asks you to close it, close the window, launch MSYS2 UCRT64 again, and run:

```bash
pacman -Su
```

### 2. Installing required tools

Run the following command:

```bash
pacman -S --needed \
  base-devel \
  git \
  mingw-w64-ucrt-x86_64-toolchain \
  mingw-w64-ucrt-x86_64-cmake \
  mingw-w64-ucrt-x86_64-ninja \
  mingw-w64-ucrt-x86_64-qt6-base \
  mingw-w64-ucrt-x86_64-qt6-declarative \
  mingw-w64-ucrt-x86_64-qt6-tools
```

### 3. Tool versions

Tested build configuration:

| Tool | Version |
|---|---|
| GCC / G++ | 16.2.0 |
| GNU Binutils (windres) | 2.47.20260726 |
| CMake | 4.4.4 |
| Qt | 6.11.2 |
| Ninja | 1.13.2 |

Installed versions can be checked using the following commands:

```bash
g++ --version
windres --version
cmake --version
qmake6 --version
ninja --version
```

### 4. Building the project

Navigate to the project root directory and configure the build:

```bash
cmake -S . -B build -G Ninja \
  -DCMAKE_BUILD_TYPE=Release \
  -DGERBER_NATIVE_MARCH=OFF \
  -DCMAKE_RC_FLAGS="--use-temp-file"
```

The `--use-temp-file` option is required for correct processing of Windows resource files (`.rc`) using GNU windres.

Start the build:

```bash
cmake --build build --parallel 12
```

After a successful build, the executable can be found at:

```text
bin/Qt6._GNU_Release_x64/bin/GGEasy.exe
```

### Notes

- Make sure to use the **MSYS2 UCRT64** terminal.
- Close any running instance of `GGEasy.exe` before rebuilding. Otherwise, Windows may prevent DLL files from being overwritten.
- If a `Permission denied` error occurs while creating a DLL, check whether the corresponding file is being used by another process.

![Window](Window.PNG)

---