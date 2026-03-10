# CorePost Project  
*Data leaks don't ask permission.*

---

## 🇷🇺 Описание проекта

### 🔐 Что такое CorePost?

**CorePost** — это модульная система защиты корпоративных устройств от несанкционированного доступа, утечек данных и краж. Решение построено на принципах **Zero Trust**, **многофакторной аутентификации** и **гибкой кастомизации под инфраструктуру заказчика**.

![CorePostRegistrationRu](https://github.com/user-attachments/assets/7ca9593d-2a8e-44e5-a2f6-bc21fb1a9a55)
![CorePostUsageRu](https://github.com/user-attachments/assets/d3fa0012-cab9-4eaf-853d-557fb1e91589)
![CorePostMaliciousRu](https://github.com/user-attachments/assets/dcb8fc3e-679f-433b-a67d-8e236f32961e)

---

### ✅ Основные цели

- Полная защита шифрованного диска **до загрузки операционной системы**  
- Реакция на инциденты в **реальном времени** через panic-интерфейс  
- **Удалённое управление доступом** через безопасный внутренний сервер  
- **Локальность, независимость от облаков и сторонних вендоров**  
- Масштабируемость и гибкая настройка под любые требования компании

---

### 🧠 Философия CorePost

> **"Не доверяй — проверяй. Даже своему железу."**  
> Каждый ноутбук, каждое устройство рассматривается как потенциально скомпрометированное.  
> Только валидация по всем факторам (сеть, ключ, пароль, сервер) позволяет получить доступ к данным.

---

### 🧩 Уникальные возможности

- **3-факторная авторизация** (пароль, USB-ключ, сетевой токен)
- **Panic-кнопка на мобильном** — сотрудник может немедленно пометить устройство как "украденное"
- Полностью **локальный сервер** на FastAPI, не требующий интернета
- Автономная работа **initramfs** с сетевой проверкой доступа
- **daemon**, работающий на уровне `init`, невидимый и неубиваемый
- Поведение при утрате связи: **гибкая реакция** (выключение, задержка, игнор)
- Поддержка **whitelist'ов, регистрационных хэшей и конфигурационных политик**

---

### 🔄 Масштабируемость и кастомизация

- Инсталляция с `.conf`-файлом, содержащим всю необходимую логику политики безопасности  
- Поддержка централизованных политик и кастомных скриптов при установке  
- Простая интеграция в существующую корпоративную инфраструктуру (в том числе в офлайн-сегменты)

---

### 🛠 Компоненты системы

| Компонент     | Назначение                                        |
|---------------|---------------------------------------------------|
| `initramfs`   | Preboot-окружение, проверка сети, токенов, монтирование |
| `install`     | Установщик + генерация ключей, конфигов и привязки |
| `daemon`      | Фоновый агент, проверка статуса устройства        |
| `server`      | Выдача токенов, регистрация устройств, panic API |
| `mobile`      | Приложение тревожной кнопки                       |

---

### 🆚 Сравнение с аналогами

| Возможность                      | CorePost | BitLocker | LUKS + Clevis | Symantec |
|----------------------------------|----------|-----------|----------------|----------|
| Panic-кнопка                     | ✅       | ❌        | ❌             | ❌       |
| 3FA (USB + password + net)       | ✅       | ⚠️ TPM    | ❌             | ⚠️       |
| Работает до загрузки ОС          | ✅       | ✅        | ✅             | ✅       |
| Полная локальность               | ✅       | ❌ (Intune) | ⚠️             | ❌       |
| Open-source                      | ✅       | ❌        | ✅             | ❌       |
| Масштабируемая архитектура       | ✅       | ⚠️        | ❌             | ⚠️       |

---

## 🇬🇧 English Description

### 🔐 What is CorePost?

**CorePost** is a modular system for **enterprise device protection**. It prevents unauthorized access, mitigates data leakage, and allows instant remote device lockdowns using **multi-factor authentication**, **pre-boot disk encryption** and a **panic-button interface**.

![CorePostRegistrationGb](https://github.com/user-attachments/assets/2ecd66a1-3c24-4e9b-8ff5-2b3cbaed2e3c)
![CorePostUsageGb](https://github.com/user-attachments/assets/e43c27f2-3528-4844-8827-0c29dc0856ec)
![CorePostMaliciousGb](https://github.com/user-attachments/assets/cddc6ad7-40ab-425d-943c-0fc8d41682b5)

---

### ✅ Key Goals

- Protect encrypted disks **before OS boots**
- Respond to theft or loss with a **mobile panic button**
- **Fully offline-capable**, using local server logic
- Designed around **Zero Trust** principles
- Highly **customizable and scalable** for any organization

---

### 🧠 Core Philosophy

> **"Assume breach. Trust no endpoint."**  
> Every device is untrusted until it proves otherwise — through **password**, **hardware key**, and **real-time network verification**.

---

### 🧩 Unique Features

- **3FA preboot unlock** (password + USB key + remote server)
- **Mobile panic app** for instant lockdown
- Local-only **FastAPI server** — no cloud required
- Full control over **offline policies** and server behavior
- A **daemon embedded into init**, designed to be unkillable
- USB validation (non-clonable where supported)
- Network-verifiable unlock tokens

---

### 🔄 Scalability & Customization

- Configurable installer with `.conf` file for security policies  
- Modular architecture — swap/extend components per use case  
- Corporate deployment with whitelisting, hardware-bound keys, key revocation

---

### 🛠 System Components

| Component     | Purpose                                  |
|---------------|------------------------------------------|
| `initramfs`   | Preboot shell + unlock logic             |
| `install`     | Configurable installer & registration    |
| `daemon`      | Root-level agent for device status       |
| `server`      | Token management + panic control         |
| `mobile`      | Panic-button companion app               |

---

### 🆚 Compared to other solutions

| Feature                         | CorePost | BitLocker | LUKS + Clevis | Symantec |
|----------------------------------|----------|-----------|----------------|----------|
| Panic button                    | ✅       | ❌        | ❌             | ❌       |
| 3FA (USB + password + net)      | ✅       | ⚠️ TPM    | ❌             | ⚠️       |
| Pre-boot protection             | ✅       | ✅        | ✅             | ✅       |
| Fully offline-capable           | ✅       | ❌ (cloud) | ⚠️             | ❌       |
| Open-source                     | ✅       | ❌        | ✅             | ❌       |
| Designed for scalability        | ✅       | ⚠️        | ❌             | ⚠️       |

---

## 📁 Репозиторий

Реализация проекта доступна в виде отдельных модулей:

```
📦 /corepost-initramfs
📦 /corepost-daemon
📦 /corepost-server
📦 /corepost-install
📦 /corepost-mobile
```

---

## 🧩 Status: Active R&D

Проект находится в активной разработке.  

---

**CorePost Project**  
*Data leaks don't ask permission.*
