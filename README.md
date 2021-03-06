# AiMatter
Тестовое задание для компании AiMatter:
Натренировать сеть, предсказывающую наличие тех или иных признаков по фото на основе CelebA датасета (очки, шляпа, усы, улыбка).
Вот тут есть картинки и 40 бинарных признаков: http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html
Ожидаемый результат: код на гитхаб, необходимый для тренировки такой сети.

Решение реализовано в виде блокнотов для Jupiter. Для запуска необходимо иметь установленными библиотеки keras и Theano для python 3.5
Т.к. для решения задачи использовался компьютер на процессоре I7 с 16 Gb памяти без внешнего графического ускорителя, все входные данные
были преобразованы в чернобелые с разрешением 128 на 128 пикселей. В обучении и тестировании использовались только изображения 5 классов:
улыбка, очки, борода, в шляпе, нейтрально без их комбинаций. Суммарно 10000 объектов в обучающей выборке по 2000 каждого типа, 2000 в валидационной выборке
и 400 для тестовой выборки.
Утилиты для конверсии собраны в блокноте: 1 Dataset Preparation.ipynb 

Решение на основе SVN достигло точности в 65,65% на валидационной выборке. 
Блокнот: 2 Training SVM model.ipunb

Бинарный классификатор на MLP 72,95% на валидационной выборке.
Блокнот: 2 Training MLPClassifier.ipynb

Мультиклассовый классификатор на MLP с использованием библиотеки keras до 73.10%
Блокнот: 2 Training MLP model Keras.ipynb

Простая сверточная сеть описанная в книге Neural Networks and Deep Learning by Michael Nielsen реализованная на keras до 85.15%
Блокнот: 2 Nielsen like Keras.ipynb

Урезанная до нескольких первых и последних каскадов VGG подобная архитектура дала до 87% правильно определенных объектов.
Блокнот: 2 VGG like Keras.ipynb

Выводы: К сожалению, время общета 1 эпохи даже для сильно упрощенной VGG подобной архитектуры на чернобелых ужатых фотографиях 
составляло 30 минут. Это не дало возможности получить точность классификации выше 90% за преемлемое время.
Приналичии графического ускорителя и большего объема памяти для решения данной задачи следует применит  полноценную VGG на цветных снимках.
Ожидаемая точность классификации вероятно будет выше 95%. Как вариант можно с высоким разрешением вырезать области подборотка, рта, глаз
и макушки головы и проводить анализ именно их.





