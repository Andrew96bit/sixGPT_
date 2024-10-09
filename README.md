Проблема виникає через те, що SSH ключ не налаштований або не доданий до вашого облікового запису GitHub. Щоб вирішити це, вам потрібно перевірити, чи правильно налаштовано SSH ключі на VPS та GitHub. Ось кроки для вирішення:

### 1. Перевірка наявності SSH ключа на VPS:
Виконайте команду для перевірки наявних SSH ключів:

```bash
ls -al ~/.ssh
```

Якщо у списку є файли `id_rsa` та `id_rsa.pub` (або інші ключі типу ED25519), перейдіть до наступного кроку. Якщо ключів немає, створіть їх:

### 2. Створення SSH ключа:
Якщо у вас немає ключа, створіть його за допомогою цієї команди:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

(Замініть `your_email@example.com` на свою електронну пошту, зареєстровану в GitHub).

Після цього натисніть `Enter`, щоб зберегти ключ у стандартному місці (`~/.ssh/id_ed25519`), а також можете встановити пароль, якщо хочете.

### 3. Додавання публічного ключа до GitHub:
Тепер вам потрібно додати публічний ключ до вашого облікового запису GitHub. Виконайте команду для копіювання публічного ключа:

```bash
cat ~/.ssh/id_ed25519.pub
```

Скопіюйте його.

1. Увійдіть у GitHub.
2. Перейдіть до **Settings** -> **SSH and GPG keys**.
3. Натисніть на **New SSH key**, додайте назву та вставте ключ.

### 4. Перевірка підключення до GitHub:
Після додавання ключа, виконайте команду, щоб перевірити з'єднання:

```bash
ssh -T git@github.com
```

Якщо все налаштовано правильно, GitHub привітає вас повідомленням, що ви успішно підключилися.

### 5. Повторіть команду клонування:
Тепер можна повторити команду клонування:

```bash
git clone git@github.com:sixgpt/miner.git
```

-------------------------------------------------------------------------------------------------------------------------

3. Завантажте скрипт для встановлення Docker:
   ```bash
   curl -fsSL https://get.docker.com -o get-docker.sh
   ```

4. Встановіть Docker:
   ```bash
   sudo sh get-docker.sh
   ```

5. Перевірте версію Docker:
   ```bash
   docker --version
   ```

--------------------------------------------------------------------------------------------------------------------------

## Prerequisites
(1) install docker on your machine. (https://docs.docker.com/engine/install/)

(2) Fund your wallet with at least 0.1 $VANA

(3) Login with this wallet on sixgpt.xyz


## Run the miner
Clone the repository:
```
git clone git@github.com:sixgpt/miner.git
cd miner
```

Set the following environment variables:
```
export VANA_PRIVATE_KEY=<your_private_key>
export VANA_NETWORK=satori
```

Run the miner:
```
docker compose up
```

## Notes
- You must have logged into sixgpt.xyz with your wallet before running the miner
- Make sure the wallet associated with your vana private key has enough $VANA balance on the desired network (at least 0.1)
