Лабораторная работа №18.
Тема: Работа с кодировками
В лабораторной работе №7 изменить все использования типа данных char на wchar_t без изменений функциональности. Адаптировать работу с консольным и файловым вводом/выводом.
Работа с символьными массивами.
19. Посчитать количество слов, длина которых равна 3;

#include <stdio.h>
#include <string.h>
#include <stdbool.h>

// Функция для проверки, является ли символ буквой
bool isLetter(char c) {
    return (c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z');
}

int main() {
    char str[100]; // Максимальная длина входной строки
    int count = 0; // Счетчик слов длиной 3

    printf("Введите строку: ");
    fgets(str, sizeof(str), stdin);

    int length = strlen(str);
    bool inWord = false;
    int wordLength = 0;

    for (int i = 0; i < length; i++) {
        if (isLetter(str[i])) {
            inWord = true;
            wordLength++;
        } else {
            if (inWord && wordLength == 3) {
                count++;
            }
            inWord = false;
            wordLength = 0;
        }
    }

    // Проверка последнего слова, если оно имеет длину 3
    if (inWord && wordLength == 3) {
        count++;
    }

    printf("Количество слов длиной 3: %d\n", count);

    return 0;
}
