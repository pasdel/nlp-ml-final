# nlp-ml

Общая задача осталось прежней - классификация элементов docx документов для последующей проверки корректности оформления в соответствии с ГОСТ 7.32-2017

Датасает - создан вручную. Целевой параметр, по которому происходит классификация - CurElementMark 
Работа опирается на результаты, представленные в первом задании - https://github.com/pasdel/nlp-ml

Параметры текстовых элементов (например, цвет, выравнивание, отступ и пр.) выделялись с помощью отдельно написанного парсера.
Дополнительно были выдвинуты гипотезы, что для классификации элементов могут быть полезны такие параметры, как:
- количество слов
- последний символ параграфа
- количество спецсимволов в параграфе
- первое слово и др.
Эти параметры уже представлены в датасете.

В ходе работы было проведено большое количество экспериментов, в результате которых:
- оптимизирован датасет - увеличено число минорных классов для их большей сбалансированности. Добавленные строки в файле parsed.csv
  ![alt](https://test.teststand.ru/1.png)
- оптимизированы параметры Catboost с использованием Optuna, оценена значимость гиперпараметров (см. в приложенном final-catboost-optuna.ipynb)
  ![alt](https://test.teststand.ru/3.png)
  ![alt](https://test.teststand.ru/4.png)
- определено влияние каждого из параметров для исследуемых классов текстовых элементов документов (SHAP values)
  ![alt](https://test.teststand.ru/2.png)
- исследованы возможность и целесообразность применения LSTM для определения закономерностей в последовательности классов параграфов (по n-граммам). Результат оказался отрицательным, использование регулярных выражений более оправдано.
- по результатам исследования в соавторстве написана статья и подготовлен доклад "Document Formatting Automated Control System using LSTM and CatBoost" для международной конференции IMS-2024 (International Workshop Computational Linguistics (CompLing-2024)) Программа конфренции - https://ims.itmo.ru/File/IMS-2024_program.pdf (стр. 28)
