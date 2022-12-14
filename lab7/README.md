# Отчёт по лабораторной работе №7 по курсу “Фундаментальная информатика”

<b>Студент группы:</b> <ins>М80-108Б-22 Былькова Кристина Алексеевна, № по списку 2</ins>

<b>Контакты e-mail:</b> <ins>kristina.bilckova@yandex.ru</ins>

<b>Работа выполнена:</b> «15» <ins>октября</ins> <ins>2022</ins> г.

<b>Преподаватель:</b> <ins>асп. каф. 806 Сахарин Никита Александрович</ins>

<b>Входной контроль знаний с оценкой:</b> <ins>5 (отлично)</ins>

<b>Отчет сдан</b> «15» <ins>октября</ins> <ins>2022</ins> г., <b>итоговая оценка</b> <ins>5 (отлично)</ins>

<b>Подпись преподавателя:</b> ___________


## 1. Тема
Программирование в алгоритмической модели Маркова.
## 2. Цель работы
Составить программу для выполнения поставленной задачи.
## 3. Задание (вариант № 11)
Входное слово представляет собой два двоичных числа без знака, разделенные знаком "*". Составить алгоритм вычисления двоичного арифметического сдвига второго числа влево на число разрядов, равное первому числу.
## 4. Оборудование:
<b>Процессор:</b> AMD Ryzen9-5900HS, 8 ядер

<b>ОП:</b> 16gb

<b>SSD:</b> 1 Tb SSD

<b>Монитор:</b> 15.6" - 2560x1440

<b>Графика:</b> NV GeForce RTX 3080

## 5. Программное обеспечение:
<b>Операционная система семейства:</b> VirtualBox 6.1.38 - Ubuntu 22.04.01 LTS

<b>Интерпретатор команд:</b> -

<b>Система программирования:</b> -

<b>Редактор текстов:</b> -

<b>Утилиты операционной системы:</b> -

<b>Прикладные системы и программы:</b> Интерпретатор алгоритмов Маркова nam.

<b>Местонахождение и имена файлов программ и данных на домашнем компьютере:</b> /home/kristina

## 6. Идея, метод, алгоритм решения задачи (в формах: словесной, псевдокода, графической [блок-схема, диаграмма, рисунок, таблица] или формальные спецификации с пред- и постусловиями)
Создаём метасимволы в начале и конце исходных данных "%" и "_" соответственно. Создаём метасимвол ">" для движения вправо и "<" для движения влево. Декрементируем первое число и каждый раз приписываем в конец второго "0".
## 7. Сценарий выполнения работы [план работы, первоначальный текст программы в черновике (можно на отдельном листе) и тесты либо соображения по тестированию].
Выполнение на примере:
| № | Начальная лента | Конечная лента |
| ------ | ------ | ------ |
| 1 | 1*101 | 1(*)101 |
| 3 | 1(*)101 | (1*)101 |
| 4 | (1*)101 | (1*1)01 |
| 5 | (1*1)01 | (1*10)1 |
| 6 | (1*10)1 | (1*101) |
| 7 | (1*101) | %1*101) |
| 8 | %1*101) | %1*101_ |
| 9 | %1*101_ | %>1*101_ |
| 10 | %>1*101_ | %1>*101_ |
| 11 | %1>*101_ | %0!*101_ |
| 12 | %0!*101_ | %0*!101_ |
| 13 | %0*!101_ | %0*1!01_ |
| 14 | %0*1!01_ | %0*10!1_ |
| 15 | %0*10!1_ | %0*101!_ |
| 16 | %0*101!_ | %0*1010<_ |
| 17 | %0*1010<_ | %0*1010<_ |
| 18 | %0*1010<_ | %0*101<0_ |
| 19 | %0*101<0_ | %0*10<10_ |
| 20 | %0*10<10_ | %0*1<010_ |
| 21 | %0*1<010_ | %0*<1010_ |
| 22 | %0*<1010_ | %0>*1010_ |
| 23 | %0>*1010_ | %#0*1010_ |
| 24 | %#0*1010_ | -0*1010_ |
| 25 | -0*1010_ | -0*1010_ |
| 26 | -0*1010_ | 0*1010_ |
| 27 | 0*1010_ | 0*1010 |

Пункты 1-7 отчета составляются сторого до начала лабораторной работы.
Допущен к выполнению работы.  
<b>Подпись преподавателя:</b> _____________________

## 8. Распечатка протокола 

```
1(->(1
0(->(0
)1->1)
)0->0)

(->%
)->_

%#0->-0
-0*->0*
-0->-

>1->1>
>0->0>

1>*->0!*

0>*->#0*
0#->#0
1#->0=
#0->1=
=0->1=

1=*->1*!
0=*->0*!

0!*->0*!
1!*->1*!

%#0->0#

!1->1!
!0->0!

1!_->10<_
0!_->00<_

0<-><0
1<-><1

*<->>*

%->%>

0_->.0
1_->.1

*->(*)
```

## 9. Дневник отладки должен содержать дату и время сеансов отладки и основные события (ошибки в сценарии и программе, нестандартные ситуации) и краткие комментарии к ним. В дневнике отладки приводятся сведения об использовании других ЭВМ, существенном участии преподавателя и других лиц в написании и отладке программы.

| № |  Лаб. или дом. | Дата | Время | Событие | Действие по исправлению | Примечание |
| ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| 1 | дом. | 15.10.22 | 13:00 | Выполнение лабораторной работы | - | - |
## 10. Замечания автора по существу работы — Двоичный арифметический сдвиг второго числа влево на число разрядов, равное первому числу.
Двоичный арифметический сдвиг второго числа вправо на число разрядов, равное первому числу.
```
(#0->0end
end0->end
end*->*con

con0->0con
con1->1con
con)->.

>1->1>
>0->0>

1>*->0*!
0>*->#0*
0#->#0
1#->0=
#0->1=
=0->1=

1=*->1*!
0=*->0*!

*!1->*+11
*!0->*+00
+1->1+
+0->0+

1+)-><)
0+)-><)

1<-><1
0<-><0

*<->>*

0(->(0
1(->(1
)0->0)
)1->1)

(0->(>0
(1->(>1


*->(*)

)->
end*->.*
```
## 11. Выводы
Были изучены базовые команды для написания программы в алгоритмической модели Маркова. Был продуман и написан алгоритм для выполнения лабораторной работы. Были приобретены навыки, необходимые для дальнейшего обучения.

Недочёты при выполнении задания могут быть устранены следующим образом: —

<b>Подпись студента:</b> _________________


