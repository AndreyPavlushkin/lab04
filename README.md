# Отчёт по лабораторной работе №4


## Что сделал

### 1. Создал репу `lab04` с лицензией MIT

- Залетел на GitHub, сделал публичную репу `lab04`.
- Поставил галку на `README.md`, выбрал лицензию MIT.
- Скрин:

![Создание репы](image.png)

### 2. Сгенерил токен для GitHub с правами `repo`

- В настройках GitHub создал токен с доступом к репозиториям (`repo`).
- Скрин:

![Токен](image-1.png)

### 3. Настроил Git и hub

- Задал переменные, настроил `hub` для работы с GitHub.
- Команды:

```powershell
$env:GITHUB_USERNAME = "AndreyPavlushkin"
$env:GITHUB_EMAIL = "pavlushkinandrey201712@gmail.com"
$env:GITHUB_TOKEN = "github_pat_11BOQHPCY02q2tp7Evjfmw_6k9ik8YoYv********************************************"
$edit = "notepad"

mkdir C:\Users\serqw\labO4\lab04
cd C:\Users\serqw\labO4\lab04

mkdir $env:USERPROFILE\.config
@"
github.com:
- user: $env:GITHUB_USERNAME
  oauth_token: $env:GITHUB_TOKEN
  protocol: https
"@ | Out-File -FilePath $env:USERPROFILE\.config\hub -Encoding UTF8
git config --global hub.protocol https
```

- Скрин:

![Настройка hub](image-2.png)

### 4. Добавил `.gitignore`

- На GitHub создал `.gitignore` с таким содержимым:

```
*build*/
*install*/
*.swp
.idea/
```

- Закоммитил с сообщением "Add .gitignore".
- Скрин:

![.gitignore](image-3.png)

### 5. Создал структуру проекта и файлы

- Сделал папки: `sources`, `include`, `examples`.
- Команда:

```powershell
cd C:\Users\serqw\labO4\lab04
New-Item -ItemType Directory -Path sources,include,examples
```

- Добавил файлы:

#### `sources/print.cpp`

```cpp
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
```

- Команда:

```powershell
@"
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
"@ | Out-File -FilePath sources/print.cpp -Encoding UTF8
```

- Скрин:

![print.cpp](image-4.png)

#### `include/print.hpp`

```cpp
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
```

- Команда:

```powershell
@"
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
"@ | Out-File -FilePath include/print.hpp -Encoding UTF8
```

- Скрин:

![print.hpp](image-5.png)

#### `examples/example1.cpp`

```cpp
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
```

- Команда:

```powershell
@"
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
"@ | Out-File -FilePath examples/example1.cpp -Encoding UTF8
```

- Скрин:

![example1.cpp](image-6.png)

#### `examples/example2.cpp`

```cpp
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
```

- Команда:

```powershell
@"
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
"@ | Out-File -FilePath examples/example2.cpp -Encoding UTF8
```

- Скрин:

![example2.cpp](image-7.png)

### 6. Закоммитил и запушил

- Проверил статус, добавил файлы, закоммитил и запушил в `main`.
- Команды:

```powershell
git status
git add .
git commit -m "added sources"
git push origin main
```

- Скрин:

![Коммит и пуш](image-8.png)

### 7. Сделал отчёт

- Склонировал репу `tp-labs/lab04` для шаблона.
- Создал `REPORT.md`.
- Команды:

```powershell
cd C:\Users\serqw\labO4
$env:LAB_NUMBER = "04"
git clone https://github.com/tp-labs/lab$env:LAB_NUMBER.git tasks/lab$env:LAB_NUMBER
mkdir reports/lab$env:LAB_NUMBER
Copy-Item tasks/lab$env:LAB_NUMBER/README.md reports/lab$env:LAB_NUMBER/REPORT.md
cd reports/lab$env:LAB_NUMBER
notepad REPORT.md
```


