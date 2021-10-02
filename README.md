# Twitter-vs-Bitcoin

По ссылке https://drive.google.com/drive/folders/12cFd9pmwBiQfuZQaX1NpfDBFoHQehqRq?usp=sharing:
1) Минутные данные по ценам и объемам торгов BTC/USD
2) ~1.5 млн. твитов
3) reddit/twitter with sentiment - основной массив данных + расчитанные сентименты
4) reddit/twitter with PCA - reddit/twitter with sentiment + PCA на feature extraction
5) reddit/twitter total X - reddit/twitter with PCA из которого мы взяли перекрестные произведения 2 переменных или квадрат одной
6) xgboost auto ml MAPE - MAPE для каждой отдельной переменной reddit/twitter total X 
7) instr - набор переменных, отобранный AUTO ML из пункта 5. Part 2.1

Part 1.
1) Парсинг твиттера и реддита
2) EDA по соотнисению численных переменных и сентиментов с доходностью и объемами торгов не даёт результатов.
3) |Корреляция|<0.1

Part 2.1.
Для каждого формата reddit (Daily, hourly, minutely):
1) Расчет сентиментов
2) Feature extraction - FeatureHasher/CountVectorizer/bigram_vectorizer
3) PCA для каждой переменной - 30 компонент
4) Сочетание переменных - перекрестные произведения 2 переменных или квадрат одной
5) AUTO ML - xgboost - для Daily формата на всей выборке, для остальных - на 30% наблюдений:
I) для каждой переменный расчитываем MAPE
II) сортируем массив переменных по возвостанию MAPE
III) увеличиваем набор переменных, поочередно включая новую, если её VIF<5

Для twitter :
1) Feature extraction - FeatureHasher/CountVectorizer/bigram_vectorizer
2) PCA для каждой переменной - 30 компонент
3) Сочетание переменных - перекрестные произведения 2 переменных или квадрат одной
