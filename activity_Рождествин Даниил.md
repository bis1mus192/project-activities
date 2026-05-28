# Диаграмма деятельности: Снятие наличных в банкомате

## Описание процесса
Клиент вставляет банковскую карту, вводит PIN-код, выбирает сумму снятия.  
Система проверяет корректность PIN и достаточность средств на счёте.  
Если проверки пройдены, банкомат выдаёт деньги и одновременно печатает чек и обновляет баланс счёта.  
При ошибке PIN или нехватке средств процесс прерывается с выдачей карты и соответствующим сообщением.

## Диаграмма

```mermaid
graph TD
    Start([Начало]) --> InsertCard(Вставить карту)
    InsertCard --> EnterPIN(Ввести PIN)
    EnterPIN --> CheckPIN{PIN верен?}
    CheckPIN -- Нет --> ShowError(Показать сообщение об ошибке)
    ShowError --> EjectCard(Выдать карту)
    CheckPIN -- Да --> EnterAmount(Ввести сумму снятия)
    EnterAmount --> CheckBalance{Достаточно средств?}
    CheckBalance -- Нет --> ShowInsufficient(Сообщение: Недостаточно средств)
    ShowInsufficient --> EjectCard
    CheckBalance -- Да --> DispenseCash(Выдать деньги)
    DispenseCash --> Fork{Разделение}
    Fork --> PrintReceipt(Печать чека)
    Fork --> UpdateBalance(Обновить баланс счёта)
    PrintReceipt --> Join(Слияние)
    UpdateBalance --> Join
    Join --> EjectCard
    EjectCard --> End([Конец])
