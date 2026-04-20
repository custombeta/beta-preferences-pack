# betaDropDownPreference
Компонент выпадающего списка, сохраняющий состояние напрямую в `System table`. Поддерживает сброс до значения по умолчанию долгим нажатием.

## Установка
 1. Импортируйте архив в любой `.dex`
 2. Добавьте строковый ресурс в `string-ru`, для работы уведомления:
```xml
<string name="beta_default_value_restored">Значение по умолчанию восстановлено</string>
```

## Поддерживаемые атрибуты
| Атрибут                | Обязательный | Тип данных     | Описание и что сохраняет |
|------------------------|--------------|----------------|--------------------------------------------------------------------------------------------------------|
| `android:title`        | Нет          | `String`       | Название настройки в интерфейсе.                                                                       |
| `android:summary`      | Нет          | `String`       | Описание настройки под названием.                                                                      |
| `android:key`          | Да           | `String`       | Ключ системной настройки. По этому ключу в `System table` будет сохраняться числовое значение массива. |
| `android:defaultValue` | Да           | `String`       | Значение по умолчанию. Используется при первом запуске и восстанавливается при сбросе.                 |
| `app:entries`          | Да           | `String array` | Массив строк для отображения пользователю (названия пунктов в списке).                                 |
| `app:entryValues`      | Да           | `String array` | Массив значений, соответствующих пунктам из entries. Именно они сохраняются в `System table`.          |

## Пример массивов
```xml
<string-array name="your_entries_array">
    <item>Первый пункт</item>
    <item>Второй пункт</item>
    <item>Третий пункт</item>
</string-array>

<string-array name="your_values_array">
    <item>0</item>
    <item>1</item>
    <item>2</item>
</string-array>
```

## Использование в XML
```xml
<betaDropDownPreference
    android:title="Название настройки"
    android:summary="Описание настройки"
    android:key="your_key"
    android:defaultValue="2"
    app:entries="@array/your_entries_array"
    app:entryValues="@array/your_values_array" />
```
