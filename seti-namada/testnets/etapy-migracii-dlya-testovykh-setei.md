# Этапы миграции для тестовых сетей

Это руководство поможет вам перенести узел валидатора из одной тестовой сети в другую. Эти шаги являются необязательными, и для большинства тестовых сетей они не понадобятся.

### Переустановка узла валидатора (необязательно)&#x20;

{% hint style="info" %}
<mark style="color:blue;">С выходом версии</mark> <mark style="color:blue;"></mark><mark style="color:blue;">`0.19.0`</mark> <mark style="color:blue;"></mark><mark style="color:blue;">мы ввели обязательные ключи для валидаторов. Этими ключами являются</mark> <mark style="color:blue;"></mark><mark style="color:blue;">`eth_hot_key`</mark> <mark style="color:blue;"></mark><mark style="color:blue;">и</mark> <mark style="color:blue;"></mark><mark style="color:blue;">`eth_cold_key`</mark><mark style="color:blue;">, которые используются для работы с мостом Ethereum.</mark>
{% endhint %}

#### Найдите базовый каталог namada&#x20;

В зависимости от того, из какой тестовой сети вы мигрируете, базовый каталог будет находиться в разных местах. По этой причине мы сохраним путь к базовому каталогу в переменной.

#### До версии `0.15.3`&#x20;

Если вы мигрируете из тестовой сети ДО версии `0.15.3`, то ваш домашний каталог и соответствующие файлы будут располагаться в каталоге `.namada`. Расположение этого каталога зависит от того, где вы первоначально выполнили команду n`amadac utils join-network --chain-id <CHAIN_ID> --genesis-validator` . Он будет находиться в каталоге, в котором была выполнена эта команда.

После нахождения путь к базовому каталогу можно сохранить в переменной. Например, если команда `join-network` была выполнена из домашнего каталога, то можно выполнить команду:

```rust
export BASE_DIR=$HOME/.namada
```

#### После версии `0.15.3`&#x20;

Если вы переходите из тестовой сети ПОСЛЕ версии `0.15.3`, то ваш базовый каталог и соответствующие файлы будут находиться в `.local/share/namada` в Linux и `Library/Application Support/Namada` в MacOS. Проверить каталог по умолчанию на вашей машине можно, выполнив команду:

```
export BASE_DIR=$(namadac utils default-base-dir)
```

{% hint style="info" %}
<mark style="color:blue;">Технически правильным каталогом будет тот, который назначен переменной</mark> <mark style="color:blue;"></mark><mark style="color:blue;">`$XDG_DATA_HOME`</mark><mark style="color:blue;">, но если вы не задали эту переменную, то по умолчанию будет использоваться тот, который указан выше.</mark>
{% endhint %}

### ВАЖНО! Сохраните папку pre-genesis в каталоге базы

Прежде чем удалять какие-либо папки, следует убедиться, что мы сохранили папку pre-genesis. В этой папке содержатся ключи валидатора, и мы хотим быть уверены, что не потеряем их.

```rust
mkdir $HOME/backup-pregenesis && cp -r $BASE_DIR/pre-genesis $HOME/backup-pregenesis/
```

### Обеспечьте сохранение ключей

`ls backup-pregenesis` должен выводить сохраненный `wallet.toml`.

### Удалите базовый каталог

```rust
rm -rf $BASE_DIR/*
```

### Проверьте корректность бинарных файлов namada и cometbft.

`namada --version` вывод `v0.22.0` и `cometbft version` вывод `0.37.2`

### Создание каталога pre-genesis&#x20;

```rust
mkdir $BASE_DIR/pre-genesis
```

#### Скопируйте резервный файл обратно в папку `$BASE_DIR/pre-genesis`&#x20;

```rust
cp -r backup-pregenesis/* $BASE_DIR/pre-genesis/
```

Теперь вы должны быть готовы к работе!ru
