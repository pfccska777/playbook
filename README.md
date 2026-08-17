Создай:

```bash
cd playbook
nano README.md
```

И вставь:

````markdown
# Ansible Playbook

Playbook для установки и настройки:

- ClickHouse
- Vector
- LightHouse

## Requirements

- Ansible
- Доступ по SSH к целевым хостам

## Установка ролей

Перед запуском playbook необходимо установить роли из `requirements.yml`:

```bash
mkdir -p roles
ansible-galaxy install -r requirements.yml -p roles
````

Используются роли:

* ClickHouse — `AlexeySetevoi/ansible-clickhouse`
* Vector — `pfccska777/vector-role`
* LightHouse — `pfccska777/lighthouse-role`

## Inventory

Хосты задаются в:

```text
inventory/prod.yml
```

Используются группы:

```text
clickhouse
vector
lighthouse
```

## Проверка синтаксиса

```bash
ansible-playbook -i inventory/prod.yml site.yml --syntax-check
```

## Запуск playbook

```bash
ansible-playbook -i inventory/prod.yml site.yml
```

## Структура

```text
.
├── group_vars/
├── inventory/
│   └── prod.yml
├── templates/
│   └── nginx.conf.j2
├── requirements.yml
├── site.yml
└── README.md
```

````

Потом:

```bash
git add README.md
git commit -m "Add README"
git push
````

И проверить:

```bash
git status
```

Должно быть:

```text
nothing to commit, working tree clean
```
