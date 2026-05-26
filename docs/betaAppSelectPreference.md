# betaAppSelectPreference
Компонент выбора установленного приложения из диалогового списка, сохраняющий имя пакета выбранного приложения (`packageName`) напрямую в `System table`. Поддерживает фильтрацию по типу приложений и сброс до значения по умолчанию долгим нажатием.

## Установка
 1. Импортируйте архив в любой `.dex`
 2. Добавьте строковые ресурсы в `string-ru`, для работы уведомления и диалога:
```xml
<string name="beta_default_value_restored">Значение по умолчанию восстановлено</string>
<string name="dialog_close_button">Закрыть</string>
<string name="dialog_save_button">Сохранить</string>
```
 3. Добавьте кастомный layout `beta_app_select_item.xml` по пути `res/layout/`, также добавьте в ресурсы `layout`:
```xml
<path name="beta_app_select_item">res/layout/beta_app_select_item.xml</path>
```
 4. Опционально: добавьте drawable `beta_app_select_effect_fg.xml` в `res/drawable/` и `res/drawable-night/`, также добавьте в ресурсы `drawable`:
```xml
<path name="beta_app_select_effect_fg">res/drawable/beta_app_select_effect_fg.xml</path>
```
```xml
<path name="beta_app_select_effect_fg">res/drawable-night/beta_app_select_effect_fg.xml</path>
```
Нужен для эффекта выделения при нажатии на элемент списка. Если не добавляете — удалите строку `android:foreground="@drawable/beta_app_select_effect_fg"` из `beta_app_select_item.xml`.

## Поддерживаемые атрибуты
| Атрибут                | Обязательный | Тип данных | Описание и что сохраняет                                                                                                    |
|------------------------|--------------|------------|-----------------------------------------------------------------------------------------------------------------------------|
| `android:title`        | Нет          | `String`   | Название настройки в интерфейсе. Используется также как заголовок диалога выбора приложения.                                |
| `android:summary`      | Нет          | `String`   | Описание настройки под названием. Поддерживает форматирование текущего значения через `%s`.                                 |
| `android:key`          | Да           | `String`   | Ключ системной настройки. По этому ключу в `System table` будет сохраняться `packageName` выбранного приложения.            |
| `android:defaultValue` | Нет          | `String`   | Значение по умолчанию в виде `packageName` приложения. Используется при первом запуске и восстанавливается при сбросе.      |
| `filterFlag`           | Нет          | `Integer`  | Фильтр отображаемых приложений: `0` — все (по умолчанию), `1` — только системные, `2` — только пользовательские.            |
| `showPackageName`      | Нет          | `Boolean`  | Отображать ли имя пакета под названием приложения в списке (по умолчанию `true`).                                           |

## Использование в XML
```xml
<betaAppSelectPreference
    android:title="Выбор приложения"
    android:summary="Выбрано: %s"
    android:key="your_key"
    android:defaultValue="com.android.settings"
    filterFlag="0"
    showPackageName="true" />
```
