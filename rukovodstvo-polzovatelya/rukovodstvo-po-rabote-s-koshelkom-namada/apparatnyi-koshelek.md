# Аппаратный кошелек

Расширение веб-кошелька Namada совместимо с аппаратным обеспечением[ Ledger](https://www.ledger.com/). В данном руководстве мы рассмотрим процесс настройки устройства Ledger для работы с Namada.&#x20;

### Необходимые условия&#x20;

Устройство Ledger с установленной последней версией прошивки. Инструкции по обновлению прошивки можно [найти здесь. ](https://support.ledger.com/hc/en-us/articles/360002731113-Update-device-firmware)

Установите пакет [javascript npm здесь](https://www.npmjs.com/package/@zondax/ledger-namada).&#x20;

Для использования устройства Ledger с веб-кошельком необходимо установить [веб-кошелек Namada](veb-koshelek.md).&#x20;

### Подключение Ledger

1. Откройте веб-расширение Namada.&#x20;
2. В разделе настроек нажмите кнопку `Connect Ledger`.&#x20;
3. Задайте псевдоним для учетной записи, ключами которой будет управлять ledger.&#x20;
4. Вы можете выбрать подключение к устройству через `USB` (рекомендуется) или `HID` (Human Interface Devices).&#x20;
5. Программа запросит подтверждение подключения. Подтвердите это соединение на устройстве ledger.&#x20;
6. После этого в расширении отобразится адрес счета, ключами которого управляет устройство.&#x20;
7. Теперь можно закрыть информационное окно и использовать ledger для подписания транзакций.&#x20;

### Отправка транзакций с помощью ledger&#x20;

Инструкции по отправке транзакций с помощью веб-кошелька см. в [руководстве по веб-кошельку.](veb-koshelek.md)
