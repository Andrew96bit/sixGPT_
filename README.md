# Налаштування SixGPT майнера на VPS

## Крок 1: Створення та фінансування гаманця
1. Створіть новий **burner EVM-гаманець**.
2. Профінансуйте гаманець за допомогою [цього крана](https://faucet.vana.org/moksha).

## Крок 2: Підключення до VPS та встановлення Docker
1. Завантажте скрипт для встановлення Docker:
   ```bash
   curl -fsSL https://get.docker.com -o get-docker.sh
   ```

2. Встановіть Docker:
   ```bash
   sudo sh get-docker.sh
   ```

3. Перевірте версію Docker, щоб переконатися, що установка пройшла успішно:
   ```bash
   docker --version
   ```

## Крок 3: Клонування репозиторію
1. Клонувати репозиторій та перейти до папки:
   ```bash
   git clone https://github.com/sixgpt/miner.git
   cd miner
   ```

## Крок 4: Налаштування конфігурації
1. Відкрийте файл `docker-compose.yml` для редагування:
   ```bash
   nano docker-compose.yml
   ```

2. Змініть параметр перезапуску. Замість `restart: no` встановіть `restart: on-failure` для контейнера `sixgpt3`.

## Крок 5: Задання змінних середовища
Встановіть такі змінні середовища:

```bash
export VANA_PRIVATE_KEY=your_private_key
export VANA_NETWORK=moksha
```

## Крок 6: Запуск майнера
Запустіть майнер командою:

```bash
docker compose up
```

## Логи контейнера
Щоб переглянути логи контейнера в реальному часі, використовуйте команду:

```bash
docker compose logs -f
```

---
