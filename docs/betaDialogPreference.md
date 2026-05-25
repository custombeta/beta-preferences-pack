# betaDialogPreference
Базовый компонент для отображения произвольного диалога при нажатии на настройку. Не сохраняет значения самостоятельно — всё взаимодействие с данными реализуется через классы-слушатели кнопок. Поддерживает три кнопки: положительную, отрицательную и нейтральную.

## Установка
 1. Импортируйте архив в любой `.dex`

## Поддерживаемые атрибуты
| Атрибут           | Обязательный | Тип данных | Описание                                                                              |
|-------------------|--------------|------------|---------------------------------------------------------------------------------------|
| `android:title`   | Нет          | `String`   | Название настройки в интерфейсе.                                                      |
| `android:summary` | Нет          | `String`   | Описание настройки под названием.                                                     |
| `android:key`     | Нет          | `String`   | Ключ настройки. Компонент сам ничего не сохраняет по этому ключу.                     |

## Атрибуты для настройки диалога
| Атрибут                          | Обязательный | Тип данных | Описание                                                                                                                                   |
|----------------------------------|--------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `dialogTitle`                    | Нет          | `String`   | Заголовок диалога. Если не указан — диалог отображается без заголовка.                                                                     |
| `dialogIcon`                     | Нет          | `Drawable` | Иконка в заголовке диалога.                                                                                                                |
| `dialogLayout`                   | Нет          | `Layout`   | Ссылка на layout-ресурс (`@layout/...`), который будет встроен в тело диалога.                                                             |
| `dialogPositiveButton`           | Нет          | `String`   | Текст положительной кнопки. Кнопка не отображается, если атрибут не указан.                                                                |
| `dialogPositiveButtonListener`   | Нет          | `String`   | Полное имя класса, реализующего `DialogInterface.OnClickListener`, для положительной кнопки (например, `com.example.MyPositiveListener`).  |
| `dialogNegativeButton`           | Нет          | `String`   | Текст отрицательной кнопки. Кнопка не отображается, если атрибут не указан.                                                                |
| `dialogNegativeButtonListener`   | Нет          | `String`   | Полное имя класса, реализующего `DialogInterface.OnClickListener`, для отрицательной кнопки.                                               |
| `dialogNeutralButton`            | Нет          | `String`   | Текст нейтральной кнопки. Кнопка не отображается, если атрибут не указан.                                                                  |
| `dialogNeutralButtonListener`    | Нет          | `String`   | Полное имя класса, реализующего `DialogInterface.OnClickListener`, для нейтральной кнопки.                                                 |
| `dialogOnShowListener`           | Нет          | `String`   | Полное имя класса, реализующего `DialogInterface.OnShowListener`, вызываемого при показе диалога.                                          |
| `dialogCancelable`               | Нет          | `Boolean`  | Разрешает ли закрытие диалога нажатием вне его области или кнопкой «Назад» (по умолчанию `false`).                                         |

## Пример реализации OnClickListener
```smali
.class public Lcom/example/MyPositiveListener;
.super Ljava/lang/Object;

# interfaces
.implements Landroid/content/DialogInterface$OnClickListener;


# direct methods
.method public constructor <init>()V
    .registers 1

    invoke-direct {p0}, Ljava/lang/Object;-><init>()V

    return-void
.end method


# virtual methods
.method public onClick(Landroid/content/DialogInterface;I)V
    .registers 3

    # ваша логика

    return-void
.end method
```

## Пример реализации OnShowListener
```smali
.class public Lcom/example/MyOnShowListener;
.super Ljava/lang/Object;

# interfaces
.implements Landroid/content/DialogInterface$OnShowListener;


# direct methods
.method public constructor <init>()V
    .registers 1

    invoke-direct {p0}, Ljava/lang/Object;-><init>()V

    return-void
.end method


# virtual methods
.method public onShow(Landroid/content/DialogInterface;)V
    .registers 2

    check-cast p1, Lmiuix/appcompat/app/AlertDialog;

    # ваша логика

    return-void
.end method
```

## Использование в XML
```xml
<betaDialogPreference
    android:title="Название настройки"
    android:summary="Описание настройки"
    dialogTitle="Заголовок диалога"
    dialogIcon="@drawable/you_dialog_icon"
    dialogLayout="@layout/your_dialog_layout"
    dialogPositiveButton="Сохранить"
    dialogPositiveButtonListener="com.example.MyPositiveListener"
    dialogNegativeButton="Отмена"
    dialogNegativeButtonListener="com.example.MyNegativeListener"
    dialogNeutralButton="Сброс"
    dialogNeutralButtonListener="com.example.MyNeutralListener"
    dialogOnShowListener="com.example.MyOnShowListener"
    dialogCancelable="true" />
```
