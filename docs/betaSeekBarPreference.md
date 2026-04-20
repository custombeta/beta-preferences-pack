# betaSeekBarPreference
Компонент ползунка, сохраняющий выбранное значение напрямую в `System table` (в виде числа). Поддерживает сброс до значения по умолчанию долгим нажатием.

## Установка
 1. Импортируйте архив в любой `.dex`
 2. Добавьте строковые ресурсы в `string-ru`, для работы уведомления и отображения значения по умолчанию:
```xml
<string name="beta_default_value_restored">Значение по умолчанию восстановлено</string>
<string name="beta_seekbar_preference_default_value">Стандарт</string>
```
 3. Добавьте кастомный layout `beta_seekbar_preference.xml` по пути `res/layout/`, также добавьте в ресурсы `layout`
```xml
<path name="beta_seekbar_preference">res/layout/beta_seekbar_preference.xml</path>
```

## Поддерживаемые атрибуты
| Атрибут                | Обязательный | Тип данных | Описание и что сохраняет                                                                                                                            |
|------------------------|--------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `android:title`        | Нет          | `String`   | Название настройки в интерфейсе.                                                                                                                    |
| `android:summary`      | Нет          | `String`   | Описание настройки под названием.                                                                                                                   |
| `android:key`          | Да           | `String`   | Ключ системной настройки. По этому ключу в `System table` будет сохраняться числовое значение.                                                      |
| `android:defaultValue` | Да           | `Integer`  | Значение по умолчанию. Используется при первом запуске и восстанавливается при сбросе.                                                              |
| `max`                  | Да           | `Integer`  | Максимальное значение ползунка.                                                                                                                     |
| `min`                  | Да           | `Integer`  | Минимальное значение ползунка.                                                                                                                      |
| `step`                 | Нет          | `Integer`  | Шаг изменения значения (по умолчанию `1`).                                                                                                          |
| `showValue`            | Нет          | `Boolean`  | Если `true` — отображает текущее числовое значение рядом с ползунком (по умолчанию `true`).                                                         |
| `showDefValueText`     | Нет          | `Boolean`  | Если `true` — когда значение равно `defaultValue`, вместо числа отображается строка `beta_seekbar_preference_default_value` (по умолчанию `false`). |

## Использование в XML
```xml
<betaSeekBarPreference
    android:title="Название настройки"
    android:summary="Описание настройки"
    android:key="your_key"
    android:defaultValue="50"
    min="0"
    max="100"
    step="5"
    showValue="false"
    showDefValueText="true" />
```
