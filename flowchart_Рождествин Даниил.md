# Блок-схема алгоритма проверки числа на простоту (перебор делителей до квадратного корня)

**Описание алгоритма:**  
Алгоритм принимает целое число `n` и определяет, является ли оно простым. Если `n ≤ 1`, выводится сообщение, что число должно быть больше 1. Для `n = 2` сразу выводится «Простое». Чётные числа больше 2 считаются составными. Для нечётных чисел выполняется перебор делителей от 3 до `√n` с шагом 2. Если находится делитель, число составное, иначе — простое.

---

## Диаграмма

```mermaid
flowchart TD
    Start([Начало]) --> Input[/"Введите число n"/]
    Input --> CheckN{n > 1?}
    CheckN -- "Нет" --> Invalid[/"Вывод: Число должно быть > 1"/]
    Invalid --> Stop([Конец])
    CheckN -- "Да" --> CheckTwo{n == 2?}
    CheckTwo -- "Да" --> PrimeTwo[/"Вывод: Простое"/]
    PrimeTwo --> Stop
    CheckTwo -- "Нет" --> CheckEven{n % 2 == 0?}
    CheckEven -- "Да" --> NotPrimeEven[/"Вывод: Не простое"/]
    NotPrimeEven --> Stop
    CheckEven -- "Нет" --> Init[i = 3]
    Init --> CalcLimit["Вычислить limit = floor(√n)"]
    CalcLimit --> LoopCond{i <= limit?}
    LoopCond -- "Нет" --> PrimeFinal[/"Вывод: Простое"/]
    PrimeFinal --> Stop
    LoopCond -- "Да" --> CheckDiv{n % i == 0?}
    CheckDiv -- "Да" --> NotPrimeDiv[/"Вывод: Не простое"/]
    NotPrimeDiv --> Stop
    CheckDiv -- "Нет" --> Increment[i = i + 2]
    Increment --> LoopCond
