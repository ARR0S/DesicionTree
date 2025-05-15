# Дерево решений с нуля
Алгоритм дерева решений, написанный на Python с использованием NumPy и Pandas.
## 1. Обзор реализации
Алгоритм «Дерево решений», реализованный здесь, может настраиваться на максимальную глубину дерева решений, минимальный размер выборки, количество случайных признаков, если пользователь хочет выбрать случайным образом некоторое `d` признаков без замены при разбиении узла, и количество случайных разбиений, если пользователь хочет разбить узел на некоторое количество `` раз и выбрать лучшее разбиение среди этих `` разбиений вместо выбора лучшего разбиения среди всех потенциальных разбиений узла.

Алгоритм не может работать с наборами данных, содержащими категориальные данные, поэтому он требует их предварительной обработки, например, преобразования порядковых данных в целые числа. После преобразования всех категориальных строковых значений в наборе данных в целые числа пользователь может использовать этот набор данных в алгоритме.
## 2. Структура репозитория
```
decision-tree-from-scratch/
├── dataset_files/
│ ├──── breast_cancer.csv # UCI Breast Cancer Wisconsin (Diagnostic) Dataset
│ └──── car_evaluation.csv # UCI Car Evaluation Dataset
│
├──── decisionTree.py # Алгоритм Дерева решений
├──── breastCancer.py # Обучение и тестирование на висконсинском (диагностическом) наборе данных о раке молочной железы
└──── carEvaluation.py # Обучение и тестирование на наборе данных оценки автомобилей
```
## 3. Характеристики тестирования
- Глубина дерева решений в первый раз начинается с 1 и увеличивается на 1 до тех пор, пока точность на обучающем наборе данных не достигнет 100 %.
- НИКАКОЙ СЛУЧАЙНОСТИ. Узел разбивается по наилучшему разбиению, и все характеристики набора данных учитываются при определении наилучшего разбиения узла из всех возможных разбиений.
- Для набора данных UCI Breast Cancer Wisconsin (Diagnostic) Dataset предварительная обработка не требуется.
- Набор данных UCI Car Evalution Dataset будет предварительно обработан следующим образом.
```
«покупка": «low» -> 1, „med“ -> 2, „high“ -> 3, „vhigh“ -> 4
«maint": «low» -> 1, „med“ -> 2, „high“ -> 3, „vhigh“ -> 4
«doors": «2» -> 2, „3“ -> 3, „4“ -> 4, „5more“ -> 5
«persons": «2» -> 2, „4“ -> 4, „больше“ -> 6
«lug_boot": «small» -> 1, „med“ -> 2, „big“ -> 3
«safety": «низкий» -> 1, „средний“ -> 2, „высокий“ -> 3
```
- Соотношение обучения и тестирования для набора данных Breast Cancer Dataset установлено на уровне 3:1.
- Соотношение обучение-тест для набора данных оценки автомобилей установлено как 4:1.
## 4. Результаты на наборе данных UCI Breast Cancer Wisconsin (Diagnostic) Dataset
```
maxDepth = 1: accTest = 88.73%, accTrain = 92.51%, buildTime = 2.99s
maxDepth = 2: accTest = 88.73%, accTrain = 93.68%, buildTime = 5.37s
maxDepth = 3: accTest = 92.96%, accTrain = 97.66%, buildTime = 6.68s
maxDepth = 4: accTest = 92.96%, accTrain = 98.13%, buildTime = 6.85s
maxDepth = 5: accTest = 92.25%, accTrain = 99.30%, buildTime = 6.94s
maxDepth = 6: accTest = 92.96%, accTrain = 99.77%, buildTime = 6.89s
maxDepth = 7: accTest = 92.96%, accTrain = 100.00%, buildTime = 6.98s
```
## 5. Результаты на наборе данных UCI Car Evaluation Dataset
```
maxDepth = 1: accTest = 71.62%, accTrain = 69.34%, buildTime = 0.01s
maxDepth = 2: accTest = 77.61%, accTrain = 77.85%, buildTime = 0.02s
maxDepth = 3: accTest = 78.57%, accTrain = 79.42%, buildTime = 0.02s
maxDepth = 4: accTest = 83.78%, accTrain = 83.14%, buildTime = 0.03s
maxDepth = 5: accTest = 86.29%, accTrain = 86.69%, buildTime = 0.03s
maxDepth = 6: accTest = 93.44%, accTrain = 90.99%, buildTime = 0.05s
maxDepth = 7: accTest = 92.66%, accTrain = 93.39%, buildTime = 0.06s
maxDepth = 8: accTest = 96.14%, accTrain = 96.86%, buildTime = 0.06s
maxDepth = 9: accTest = 95.95%, accTrain = 98.68%, buildTime = 0.07s
maxDepth = 10: accTest = 97.30%, accTrain = 99.42%, buildTime = 0.08s
maxDepth = 11: accTest = 98.26%, accTrain = 99.92%, buildTime = 0.08s
maxDepth = 12: accTest = 98.46%, accTrain = 100.00%, buildTime = 0.09s
```