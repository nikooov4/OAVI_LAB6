# Лабораторная работа №6
## Сегментация текста

### Вариант 6: Персидский алфавит

### Исходные данные

- Фраза: `د و س ت ت   د ا ر م`
- Перевод фразы: `Я люблю тебя`
- Ожидаемое количество символов без пробелов: `9`
- Направление чтения: `rtl`
- Шрифт: `NotoNaskhArabic-Regular.ttf`, размер `92`
- Размер монохромного изображения: `710x110`
- Количество найденных сегментов: `9`

### Формулы профилей

```text
H(y) = sum_x I_b(x, y)
V(x) = sum_y I_b(x, y)
```

Где `I_b(x, y) = 1` для черного пикселя и `0` для белого.

### 1. Подготовка строки

#### 1.1 Монохромное изображение фразы

![input](src/input/phrase_mono.bmp)

### 2. Профили изображения

| Горизонтальный профиль | Вертикальный профиль |
|:----------------------:|:--------------------:|
| ![h](src/profiles/horizontal_profile.png) | ![v](src/profiles/vertical_profile.png) |

### 3. Сегментация символов

Сегментация выполнена на основе вертикального профиля. Пустые вертикальные промежутки используются как границы между символами. Так как персидское письмо является связным, для учебной демонстрации символы во фразе разделены пробелами.

#### 3.1 Обрамляющие прямоугольники

![boxes](src/segments/segmentation_boxes.png)

#### 3.2 Вырезанные сегменты

- Сегмент 1: ![s1](src/segments/segment_01.bmp)
- Сегмент 2: ![s2](src/segments/segment_02.bmp)
- Сегмент 3: ![s3](src/segments/segment_03.bmp)
- Сегмент 4: ![s4](src/segments/segment_04.bmp)
- Сегмент 5: ![s5](src/segments/segment_05.bmp)
- Сегмент 6: ![s6](src/segments/segment_06.bmp)
- Сегмент 7: ![s7](src/segments/segment_07.bmp)
- Сегмент 8: ![s8](src/segments/segment_08.bmp)
- Сегмент 9: ![s9](src/segments/segment_09.bmp)

#### 3.3 Массив координат прямоугольников

| idx | x0 | y0 | x1 | y1 | w | h |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 648 | 35 | 680 | 72 | 33 | 38 |
| 2 | 585 | 40 | 621 | 91 | 37 | 52 |
| 3 | 474 | 40 | 557 | 96 | 84 | 57 |
| 4 | 383 | 30 | 444 | 72 | 62 | 43 |
| 5 | 291 | 30 | 352 | 72 | 62 | 43 |
| 6 | 189 | 35 | 221 | 72 | 33 | 38 |
| 7 | 151 | 9 | 161 | 72 | 11 | 64 |
| 8 | 86 | 40 | 120 | 91 | 35 | 52 |
| 9 | 29 | 39 | 65 | 100 | 37 | 62 |

CSV с координатами (`;`-разделитель): `results/segments_boxes.csv`

### 4. Профили символов выбранного алфавита

- Эталоны символов: `src/alphabet/templates/`
- Профили X/Y: `src/alphabet/profiles/`
- Построены для всех `32` символов персидского алфавита варианта 6.

Пример — первые 8 символов:

| Символ | Эталон | Профиль X | Профиль Y |
|:------:|:------:|:---------:|:---------:|
| ا | ![t1](src/alphabet/templates/sym_01_U0627.bmp) | ![px1](src/alphabet/profiles/sym_01_U0627_profile_x.png) | ![py1](src/alphabet/profiles/sym_01_U0627_profile_y.png) |
| ب | ![t2](src/alphabet/templates/sym_02_U0628.bmp) | ![px2](src/alphabet/profiles/sym_02_U0628_profile_x.png) | ![py2](src/alphabet/profiles/sym_02_U0628_profile_y.png) |
| پ | ![t3](src/alphabet/templates/sym_03_U067E.bmp) | ![px3](src/alphabet/profiles/sym_03_U067E_profile_x.png) | ![py3](src/alphabet/profiles/sym_03_U067E_profile_y.png) |
| ت | ![t4](src/alphabet/templates/sym_04_U062A.bmp) | ![px4](src/alphabet/profiles/sym_04_U062A_profile_x.png) | ![py4](src/alphabet/profiles/sym_04_U062A_profile_y.png) |
| ث | ![t5](src/alphabet/templates/sym_05_U062B.bmp) | ![px5](src/alphabet/profiles/sym_05_U062B_profile_x.png) | ![py5](src/alphabet/profiles/sym_05_U062B_profile_y.png) |
| ج | ![t6](src/alphabet/templates/sym_06_U062C.bmp) | ![px6](src/alphabet/profiles/sym_06_U062C_profile_x.png) | ![py6](src/alphabet/profiles/sym_06_U062C_profile_y.png) |
| چ | ![t7](src/alphabet/templates/sym_07_U0686.bmp) | ![px7](src/alphabet/profiles/sym_07_U0686_profile_x.png) | ![py7](src/alphabet/profiles/sym_07_U0686_profile_y.png) |
| ح | ![t8](src/alphabet/templates/sym_08_U062D.bmp) | ![px8](src/alphabet/profiles/sym_08_U062D_profile_x.png) | ![py8](src/alphabet/profiles/sym_08_U062D_profile_y.png) |


