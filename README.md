LibrarySystemClient — Blazor-клиент для библиотеки
Веб-приложение на Blazor Server для управления библиотекой через CoreWCF-сервис.

Быстрый старт
bash
# 1. Запустить CoreWCF-сервис
cd ../peresdacha-kt4
dotnet run --project src/LibrarySystem.API

# 2. Запустить Blazor-клиент (в другом терминале)
cd ../peresdacha-kt5
dotnet run --project src/LibrarySystem.BlazorClient

# 3. Открыть браузер
http://localhost:5100

Тестовые аккаунты
Логин	Пароль	Роль
admin	admin123	Admin
librarian	lib123	Librarian
reader	read123	Reader
Эндпоинты сервиса
Транспорт	Адрес
HTTP	http://localhost:5000/LibraryService.svc
TCP	net.tcp://localhost:8090/LibraryService.svc
Переключение между протоколами — через чекбокс на страницах.

Функциональность
Страница	Reader	Librarian	Admin
Вход	✓	✓	✓
Каталог книг	просмотр	+ CRUD	+ удаление
Читатели	✗	✓	✓
Выдачи	только свои	полный доступ	✓
Статистика	✗	✓	✓
Доступные операции
Книги: поиск, добавление, редактирование, удаление (админ)

Читатели: регистрация, просмотр всех

Выдачи: выдать, вернуть, просмотр по читателю, просроченные

Статистика: общая информация о библиотеке

Структура проекта
text
src/
```
├── LibrarySystem.Contracts/      # Общие контракты и DTO
└── LibrarySystem.BlazorClient/   # Blazor Server приложение
    ├── Services/                 # WCF-клиент, сессия, ошибки
    └── Components/Pages/         # Страницы приложения
```
tests/

└── LibrarySystem.BlazorClient.Tests/  # Unit-тесты (18 тестов)
Технологии
.NET 8, Blazor Server

System.ServiceModel (WCF-клиент)

Bootstrap 5

xUnit (тестирование)

Запуск тестов
bash
dotnet test
