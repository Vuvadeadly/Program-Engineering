# Работа с серверами и протокол удаленного управления SSH

## 1. Установка SSH-клиента и генерация ключевой пары

Проверено наличие SSH-клиента в операционной системе Ubuntu с помощью команды:

```bash
ssh -V
```

Сгенерирована пара SSH-ключей алгоритма ED25519:

```bash
ssh-keygen -t ed25519 -C "gdudkin2@gmail.com"
```

При создании ключевой пары задана парольная фраза (passphrase) для защиты приватного ключа.

Для управления ключами запущен SSH-агент и добавлен приватный ключ:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Публичный ключ сохранён в директории `~/.ssh/` и выведен командой:

```bash
cat ~/.ssh/id_ed25519.pub
```

<img width="940" height="470" alt="image" src="https://github.com/user-attachments/assets/68446687-fbf8-42bd-b77b-ca9ee303331c" />

## 2. Добавление публичного ключа в аккаунт GitHub

Содержимое публичного ключа скопировано и добавлено в настройках GitHub.

Ключ успешно зарегистрирован в аккаунте GitHub под названием `Ubuntu_VB`.

<img width="940" height="705" alt="image" src="https://github.com/user-attachments/assets/0af8f4ca-ee8e-4211-995f-72cd9a1265f4" />

## 3. Проверка SSH-подключения к GitHub

Для проверки соединения выполнена команда:

```bash
ssh -T git@github.com
```

В результате GitHub вернул сообщение об успешной аутентификации:

```text
Hi Vuvadeadly! You've successfully authenticated,
but GitHub does not provide shell access.
```

<img width="940" height="157" alt="image" src="https://github.com/user-attachments/assets/335126c0-b4c3-462e-8213-4457f19234b9" />

## 4. Работа с удалённым репозиторием по SSH

Для проверки работы с удалённым репозиторием выполнено его клонирование с использованием SSH-адреса:

```bash
git clone git@github.com:Vuvadeadly/Program-Engineering.git
```

После успешного клонирования выполнен переход в директорию проекта:

```bash
cd Program-Engineering
```

Для проверки возможности внесения изменений создан тестовый файл:

```bash
echo "Hello World!" > ssh_test.txt
```

Файл добавлен в индекс Git и создан коммит:

```bash
git add ssh_test.txt
git commit -m "SSH"
```

Затем изменения отправлены в удалённый репозиторий:

```bash
git push
```

Отправка изменений завершилась успешно. Новая версия коммита появилась в удалённой ветке `main`.

<img width="940" height="158" alt="image" src="https://github.com/user-attachments/assets/39c7fd39-8fae-405c-944d-0e2ce43f9cc5" />

<img width="940" height="368" alt="image" src="https://github.com/user-attachments/assets/ae7a4e93-4878-4f39-8404-bb213a6efd1f" />
