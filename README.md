# StaticJinjaPlusPorts

Готовые Docker-образы для [StaticJinjaPlus](https://github.com/MrDave/StaticJinjaPlus) — генератора статических сайтов на основе Jinja2.

## Доступные версии

| Базовый образ       | Версия StaticJinjaPlus | Путь в репозитории     | Примечание                          |
|---------------------|------------------------|------------------------|-------------------------------------|
| ubuntu:22.04        | 0.1.0                  | `./0.1.0/`             | Полная версия                       |
| python:3.10-slim    | 0.1.0                  | `./0.1.0-slim/`        | Минимальная версия (~3–4× легче)    |
| ubuntu:22.04        | 0.1.1                  | `./0.1.1/`             | Полная версия                       |
| python:3.10-slim    | 0.1.1                  | `./0.1.1-slim/`        | Минимальная версия                  |
| ubuntu:22.04        | последняя              | `./latest/`            | Последняя стабильная версия         |
| python:3.10-slim    | последняя              | `./slim/`              | Последняя минимальная версия        |


## Как использовать

1. Склонируйте/скачайте репозиторий и перейдите в его корневую папку

```bash
git clone https://github.com/Harpins/StaticJinjaPlusPorts.git
```

2. Проведите сборку требуемого образа

```bash
docker build -t your_tag:version image_folder
```

конкретный пример:

```bash
docker build -t repository/staticjinjaplus:0.1.0 0.1.0
```

3. Запустите образ

### Быстрый тест с дефолтными примерами из образа

Создайте пустую папку `.\build` для результатов

```powershell
New-Item -ItemType Directory -Force -Path .\build
```

Выполните команду:

```powershell
docker run --rm `
  -v "${PWD}\build:/app/build" `
  your_tag:version
```

### Запуск со своими шаблонами

Предварительно в текущей директории создайте папку `.\my-site` и поместите в нее ваши шаблоны, а также пустую папку `.\output`, куда будет сложен результат

```powershell
New-Item -ItemType Directory -Force -Path .\my-site, .\output
```

Выполните команду:

```powershell
docker run --rm `
  -v "${PWD}\my-site:/app/my-site" `
  -v "${PWD}\output:/app/output" `
  your_tag:version `
  my-site --outpath output
```

Результат окажется в папке `.\output`
