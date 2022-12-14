# Отчёт по лабораторной работе №9 по курсу "Фундаментальная информатика"

<b>Студент группы:</b> <ins>М80-108Б-22 Былькова Кристина Алексеевна, № по списку 2</ins> 

<b>Контакты e-mail:</b> <ins>kristina.bilckova@yandex.ru</ins>

<b>Работа выполнена:</b> «22» <ins>октября</ins> <ins>2022</ins> г.

<b>Преподаватель:</b> <ins>асп. каф. 806 Сахарин Никита Александрович</ins>

<b>Входной контроль знаний с оценкой:</b> <ins>5 (отлично)</ins>

<b>Отчет сдан</b> «22» <ins>октября</ins> <ins>2022</ins> г., <b>итоговая оценка</b> <ins>5 (отлично)</ins>

<b>Подпись преподавателя:</b> ___________

## 1. Тема
Лабораторная работа №9 по курсу информатики
## 2. Цель работы
Составление и отладка простейшей программы на языке С итеративного характера с целочисленными рекуррентными соотношениями, задающими некоторое регулярное движение точки в целочисленной системе координат (i, j) с дискретным временем k и динамическим параметром движения l.
## 3. Задание (вариант № 2)
Кольцо, ограниченное двумя окружностями с центром в точке (10, 10), радиус внутренней окружности равен 5, а радиус внешней равен 10.

$i_0 = 0$, $j_0 = -3$, $l_0 = -7$

$i_{k+1} = \frac{|i_k - j_k + l_k|}{3 - sign(i_k - j_k + k)} + 10$

$j_{k+1} = \frac{|i_k + j_k - l_k|}{3 - sign(i_k - j_k + k)} + 10$

$l_{k+1} = max(i_kj_k, j_kl_k)(k + 1)$ $mod$ $40$
## 4. Оборудование:
<b>Процессор:</b> AMD Ryzen9-5900HS, 8 ядер

<b>ОП:</b> 16gb

<b>SSD:</b> 1 Tb SSD

<b>Монитор:</b> 15.6" - 2560x1440

<b>Графика:</b> NV GeForce RTX 3080

## 5. Программное обеспечение:
<b>Операционная система семейства:</b> VirtualBox 6.1.38 - Ubuntu 22.04.01 LTS

<b>Интерпретатор команд:</b> bash версия 4.4.19

<b>Система программирования:</b> -

<b>Редактор текстов:</b> emacs версия 25.2.2

<b>Утилиты операционной системы:</b> -

<b>Прикладные системы и программы:</b> gcc

<b>Местонахождение и имена файлов программ и данных на домашнем компьютере:</b> /home/kristina

## 6. Идея, метод, алгоритм решения задачи (в формах: словесной, псевдокода, графической [блок-схема, диаграмма, рисунок, таблица] или формальные спецификации с пред- и постусловиями)
1. Пишем функции для sigh и max;
2. Пишем цикл, изменяющий i, j, l и k по заданным правилам;
3. Если количество шагов превышает 50, то заканчиваем выполнение программы и выводим сообщение с теми значениями, при которых это произошло;
4. Если точка попадает в область, то выводим номер шага и прекращаем выполнение программы.
## 7. Сценарий выполнения работы [план работы, первоначальный текст программы в черновике (можно на отдельном листе) и тесты либо соображения по тестированию]. 
``` :src/lab9.c
#include <stdio.h>
#include <math.h>

int sign(int q) {
    if (q > 0) {
        return 1;
    }
    if (q == 0) {
        return 0;
    }
    if (q < 0) {
        return -1;
    }
}

int max(int a, int b) {
    return a > b ?  a : b;
}

int main() {
    int i = 0, j = -3, l = -7, k = 0, i1, j1;
    while (k <= 51) {
        if (k == 51) {
            printf("The point was not in the specified area. The final coordinates of the point: (%d, %d),  the value of the dynamic motion parameter: %d, the step: 50.\n", i, j, l);
            break;
        }
        if ((((i - 10) * (i - 10) + (j - 10) * (j - 10)) <= 100) && (((i - 10) * (i - 10) + (j - 10) * (j - 10)) >= 25)) {
            printf("At the step number %d the point was in the specified area.\n", k);
            break;
        }
        i1 = i;
        j1 = j;
        i = abs((i1 - j1 + l) / (3 - sign(i1 - j1 + k))) + 10;
        j = abs((i1 + j1 - l) / (3 - sign(j1 - i1 + k))) + 10;
        l = ((max(i1 * j1, j1 * l) * (k + 1)) % 40 + 40) % 40;
        k += 1;
    }
    return 0;
}
```

Пункты 1-7 отчета составляются сторого до начала лабораторной работы.
Допущен к выполнению работы.  
<b>Подпись преподавателя:</b> ________________
## 8. Распечатка протокола 
```
kristina@kristina-VirtualBox:~/Рабочий стол/lab8-9/lab9$ emacs lab9.c
kristina@kristina-VirtualBox:~/Рабочий стол/lab8-9/lab9$ cc lab9.c
kristina@kristina-VirtualBox:~/Рабочий стол/lab8-9/lab9$ ./a.out
At the step number 10 the point was in the specified area.
kristina@kristina-VirtualBox:~/Рабочий стол/lab8-9/lab9$ exit
```
## 9. Дневник отладки должен содержать дату и время сеансов отладки и основные события (ошибки в сценарии и программе, нестандартные ситуации) и краткие комментарии к ним. В дневнике отладки приводятся сведения об использовании других ЭВМ, существенном участии преподавателя и других лиц в написании и отладке программы.

| № |  Лаб. или дом. | Дата | Время | Событие | Действие по исправлению | Примечание |
| ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| 1 | дом. | 22.10.22 | 13:00 | Выполнение лабораторной работы | - | - |
## 10. Замечания автора по существу работы — Написание команд для отработки навыков работы в ОС UNIX.
Вычисление перестановки по заданному алфавиту и её порядковому номеру.
``` :src/lab9-1.c
#include <stdio.h>

#define N (4)

char alphabet[N] = { '0', '1', '2', '3' };

int permutation(int n, char result[N]);

int main(void) {
    char result[N];
    int f;
    scanf("%d", &f);
    permutation(f, result);
    printf("\n");
    for (int i = 0; i < N; ++i)
        printf("%c ", result[i]);
    return 0;
}


int permutation(int n, char result[N]) {
    int representation[4] = { 0 };
    for (int i = 1; i < N + 1; ++i) {
        representation[i - 1] = n % i;
        n /= i;
    }
    for (int i = 0; i < N; ++i)
        result[i] = alphabet[i];
    
    for (int i = N - 1; i > 0; --i) {
        int j = representation[i];
        char temp = result[j];
        for (; j < i; ++j)
            result[j] = result[j + 1];
        result[i] = temp;
    }
    for (int i = 0; i < N / 2; ++i) {
        char h = result[i];
        result[i] = result[N - i - 1];
        result[N - i - 1] = h;
    }
}
```
## 11. Выводы
Была написана и отлажены простейшая программа на языке на Си. В результате выполнения работы, были приобретены навыки, которые будут полезны для выполнения других лабораторных работ.

Недочёты при выполнении задания могут быть устранены следующим образом: —

<b>Подпись студента:</b> ____________________
