# Закрепить чат вверху списка im.recent.pin

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- нужны правки под стандарт написания
- не указаны типы параметров
- отсутствуют примеры

{% endnote %}

{% endif %}

> Scope: [`im`](../../scopes/permissions.md)
>
> Кто может выполнять метод: любой пользователь

Метод `im.recent.pin` закрепляет диалог вверху списка чатов.

## Параметры

#|
|| **Параметр** | **Пример** | **Описание** | **Ревизия** ||
|| **DIALOG_ID^*^**
[`unknown`](../../data-types.md) | `chat17`
или
`256` | Идентификатор диалога. Формат:
- **chatXXX** – чат получателя, если сообщение для чата
- **XXX** – идентификатор получателя, если сообщение для приватного диалога | 19 ||
|| **PIN**
[`unknown`](../../data-types.md) | `Y` | Закрепить или открепить диалог | 19 ||
|#

{% include [Сноска о параметрах](../../../_includes/required.md) %}

- Если указать параметр `PIN = N`, то закрепленный диалог будет откреплен.

## Примеры

{% list tabs %}

- cURL

    // пример для cURL

- JS

    ```js
    BX24.callMethod(
        'im.recent.pin',
        {
            'DIALOG_ID': 'chat17',
            'PIN': 'Y'
        },
        function(result){
            if(result.error())
            {
                console.error(result.error().ex);
            }
            else
            {
                console.log(result.data());
            }
        }
    );
    ```

- PHP

    {% include [Пояснение о restCommand](../_includes/rest-command.md) %}

    ```php
    $result = restCommand(
        'im.recent.pin',
        Array(
            'DIALOG_ID' => 'chat17',
            'PIN' => 'Y'
        ),
        $_REQUEST[
            "auth"
        ]
    );    
    ```

{% endlist %}

{% include [Сноска о примерах](../../../_includes/examples.md) %}

## Ответ в случае успеха

```json
{
    "result": true
}
```

## Ответ в случае ошибки

```json
{
    "error": "DIALOG_ID_EMPTY",
    "error_description": "Dialog ID can't be empty"
}
```

### Описание ключей

- `error` – код возникшей ошибки
- `error_description` – краткое описание возникшей ошибки

### Возможные коды ошибок

#|
|| **Код** | **Описание** ||
|| **DIALOG_ID_EMPTY** | Не передан идентификатор диалога. ||
|#