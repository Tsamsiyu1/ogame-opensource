# Introduction


# Database

Структура таблицы `ally`:

| **столбец** | **SQL тип** | **описание** |
|:-------------------|:---------------|:---------------------|
| ally_id| INT PRIMARY KEY| Порядковый номер альянса|
| tag| CHAR(8)| Аббревиатура альянса, 3-8 символов|
| name| CHAR(30)| Название альянса, 3-30 символов|
| owner_id| INT| ID основателя|
| homepage| TEXT| URL домашней страницы|
| imglogo| TEXT| URL картинки логотипа|
| open| INT| 0 - заявки запрещены (набор в альянс закрыт), 1 - заявки разрешены.|
|insertapp|INT| | 
| exttext| TEXT| Внешний текст|
| inttext| TEXT| Внутренний текст|
| apptext| TEXT| Текст заявки|
| nextrank| INT| Порядковый номер следующего ранга|
|old_tag|TEXT| |
|old_name|TEXT| |
|tag_until|INT UNSIGNED| | 
|name_until|INT UNSIGNED| |
|score1,2,3|BIGINT UNSIGNED,INT UNSIGNED,INT UNSIGNED| | 
|place1,2,3|INT,INT,INT| | 
|oldscore1,2,3|BIGINT UNSIGNED,INT UNSIGNED,INT UNSIGNED| | 
|oldplace1,2,3|INT,INT,INT| | 
|scoredate|INT UNSIGNED| |

# Ранги

  * Разрешенные символы в названии ранга: `[a-zA-Z0-9_-.]`. Макс. длина - 30 символов
  * Не более 20 рангов на альянс.

Структура таблицы `allyranks`:

| **столбец** | **SQL тип** | **описание** |
|:-------------------|:---------------|:---------------------|
|rank_id|INT|Порядковый номер ранга|
|ally_id|INT|ID альянса, которому принадлжит ранг|
|name|CHAR(30)|Название ранга|
|rights|  |Права (OR маска)|

Права:

| **маска** | **описание** |
|:---------------|:---------------------|
|0x001| Распустить альянс|
|0x002| Выгнать игрока|
|0x004| Посмотреть заявления|
|0x008| Посмотреть список членов|
|0x010| Редактировать заявления|
|0x020| Управление альянсом|
|0x040| Посмотреть статус "он-лайн" в списке членов|
|0x080| Составить общее сообщение|
|0x100| 'Правая рука' (необходимо для передачи статуса основателя)|