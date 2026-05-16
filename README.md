## Отчёт по выполнению домашнего задания к Лабораторной работе 1

### 1. Загрузка и распаковка Boost

```bash
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
mkdir ~/boost_1_69_0
tar -xzf boost_1_69_0.tar.gz -C ~/boost_1_69_0 --strip-components=1
```
Загружена версия Boost 1.69.0 и распакована в ~/boost_1_69_0.

### 2. Подсчёт файлов

```bash
find ~/boost_1_69_0 -type f | wc -l                           # 61191
find ~/boost_1_69_0 -type f \( -name "*.hpp" -o -name "*.h" -o -name "*.hxx" \) | wc -l  # 15208
find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l             # 13774
```
Остальные файлы: 61191 - 15208 - 13774 = 32209

### 3. Поиск файла any.hpp

```bash
find ~/boost_1_69_0 -name "any.hpp"
```
Найдено 10 файлов, включая boost/any.hpp, boost/hana/any.hpp, boost/fusion/include/any.hpp и др.

### 4. Поиск текста "boost::asio"

```bash
grep -rIl "boost::asio" ~/boost_1_69_0
```
Основное содержимое — в doc/html/boost_asio/example/.

### 5. Компиляция Boost

```bash
./bootstrap.sh
./b2 link=static
```
Выполнена сборка статических библиотек.

### 6. Анализ веса библиотек

```bash
mkdir ~/boost-libs
cp ~/boost_1_69_0/stage/lib/*.a ~/boost-libs/
cd ~/boost-libs
du -b *.a | sort -nr | head -10
```
Результат:
4638498	libboost_wave.a
2758078	libboost_regex.a
2289054	libboost_test_exec_monitor.a
2269102	libboost_unit_test_framework.a
2043618	libboost_locale.a
1550366	libboost_program_options.a
1192390	libboost_serialization.a
843532	libboost_graph.a
790730	libboost_wserialization.a
409384	libboost_filesystem.a
