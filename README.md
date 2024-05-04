### Описание

Легко создайте том M.2 на Synology NAS, не набирая много текста и не нуждаясь в каких-либо практических руководствах. И вам не нужны диски NVMe под торговой маркой Synology.

Этот сценарий создает RAID и пул носителей на ваших дисках NVMe, чтобы вы могли затем создать том в диспетчере хранилища.

Все, что вам нужно сделать, это запустить скрипт и ввести «да» и 1, 2, 3 или 4, чтобы ответить на несколько простых вопросов. Затем перейдите в диспетчер хранилища и выберите «Создать том».

Он также позволяет создать пул/том хранения данных, охватывающий внутренние диски NVMe и диски NVMe на карте Synology M.2 PCIe.

Для пользователей Xpenology скрипт поддерживает неограниченное количество дисков NVMe (кроме RAID 1 и Basic).

**Поддерживает DSM 7 и более поздние версии.** 

Для [DSM 6 use v1](https://github.com/007revad/Synology_M2_volume/releases/tag/v1.3.25) и запускайте ее без опции автоматического обновления.

**НОВОЕ в v2**
- Теперь отображается «Диск M.2 №» так же, как и в диспетчере хранилища.
- Теперь используется команда Synostgpool, которая позволяет следующее: (Спасибо Severe_Pea_2128 на Reddit)
  - Теперь поддерживает JBOD, SHR, SHR2 и RAID F1.
  - Добавлен выбор многотомного или однотомного пула хранения. Многотомность позволяет избыточное выделение ресурсов.
  - Добавлена ​​возможность пропустить проверку диска.
  - Больше не нужно перезагружаться после запуска скрипта.
  - Больше не нужно выполнять онлайн-сборку.
- Удален ход проверки диска, поскольку это было невозможно с помощью Synostgpool
  - Ход проверки диска можно увидеть в диспетчере хранилища.
- Удален режим пробного запуска, поскольку это было невозможно с помощью Synostgpool.
- Удалена поддержка дисков SATA M.2.
  - Если у вас есть диски SATA M.2 [use v1](https://github.com/007revad/Synology_M2_volume/releases/tag/v1.3.25) и работайте без опции автоматического обновления.

### Поддерживаемые уровни RAID

| RAID Level  | Min Drives Required  | Maximum Drives | Script version |
| ----------- |------------------|----------------|----------------|
| SHR 1       | 1 or more drives | Unlimited      | v2 and later (DSM 7 only) |
| SHR 2       | 4 or more drives | Unlimited      | v2 and later (DSM 7 only) |
| Basic       | 1 drive          | 1 drive        | all |
| JBOD        | 1 or more drives | Unlimited      | v2 and later (DSM 7 only) |
| RAID 0      | 2 or more drives | Unlimited      | all |
| RAID 1      | 2 or more drives | 4 drives       | all |
| RAID 5      | 3 or more drives | Unlimited      | all |
| RAID 6      | 4 or more drives | Unlimited      | v1.3.15 and later |
| RAID 10     | 4 or more drives | Unlimited      | v1.3.15 and later |
| RAID F1     | 3 or more drives | Unlimited      | v2 and later (DSM 7 only) |

Если выбран RAID F1, сценарий включает RAID F1 на моделях Synology, которые официально не поддерживают RAID F1.
### Подтверждено, что работаем над

<details>
  <summary>Нажмите здесь, чтобы увидеть список</summary>

| Model        | DSM version              | M.2 card  | Notes           |
| ------------ |--------------------------|-----------|-----------------|
| All          | DSM 6                    |           | [Use v1](https://github.com/007revad/Synology_M2_volume/releases/tag/v1.3.25) run without auto update option |
| RS2423+      | DSM 7.2-64570 Update 1   |           |
| DS1823xs+    | DSM 7.2-64561            | M2D20     |
| DS923+       | DSM 7.2.1-69057 Update 2 |           |
| DS923+       | DSM 7.1.1-42962 Update 5 |           |
| DS723+       | DSM 7.2.1-69057 Update 3 |           |
| DS723+       | DSM 7.2-64570 Update 1   |           |
| DS723+       | DSM 7.1.1-42962 Update 4 |           |
| DS423+       | DSM 7.2.1-69057 Update 3 |           |
| DS423+       | DSM 7.2-64570 Update 3   |           |
| DS423+       | DSM 7.1.1-42962 Update 4 |           |
| DS3622xs+    | DSM 7.2-64216 Beta       | E10M20-T1 |
| DS3622xs+    | DSM 7.1.1-42962 Update 1 |           |
| DS2422+      | DSM 7.2.1-69057 Update 4 | E10M20-T1 |
| DS1522+      | DSM 7.2.1-69057 Update 4 |           |
| DS1522+      | DSM 7.2-64570            |           |
| DS1522+      | DSM 7.1.1-42962 Update 4 |           |
| DS1821+      | DSM 7.2.1-69057 Update 4 | E10M20-T1 | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2.1-69057 Update 4 | M2D20     | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2.1-69057 Update 4 | M2D18     | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2.1-69057 Update 4 |           |
| DS1821+      | DSM 7.2.1-69057 Update 3 |           |
| DS1821+      | DSM 7.2.1-69057 Update 2 |           |
| DS1821+      | DSM 7.2.1-69057 Update 1 |           |
| DS1821+      | DSM 7.2.1-69057          |           |
| DS1821+      | DSM 7.2-64570 Update 3   |           |
| DS1821+      | DSM 7.2-64570 Update 1   | E10M20-T1 | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2-64570 Update 1   | M2D18     | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1821+      | DSM 7.2-64570 Update 1   |           |
| DS1821+      | DSM 7.2-64570            |           |
| DS1821+      | DSM 7.2-64561            |           |
| DS1821+      | DSM 7.2-64216 Beta       |           |
| DS1821+      | DSM 7.2-64213 Beta       |           |
| DS1821+      | DSM 7.1.1-42962 Update 4 |           |
| DS1621+      | DSM 7.2-64570 Update 1   | E10M20-T1 | Also needs [Synology enable_M2_card](https://github.com/007revad/Synology_enable_M2_card) |
| DS1621+      | DSM 7.2-64570 Update 1   |           |
| DS1621+      | DSM 7.1.1-42962 Update 4 |           |
| RS1221+      | DSM 7.2-64570 Update 1   | E10M20-T1 |
| RS1221+      | DSM 7.1.1                | E10M20-T1 |
| DS1520+      | DSM 7.2.1-69057 Update 2 |           |
| DS1520+      | DSM 7.2-64570 Update 1   |           |
| DS1520+      | DSM 7.1.1-42962 Update 4 |           |
| DS920+       | DSM 7.2.1-69057 Update 5 |           |
| DS920+       | DSM 7.2.1-69057 Update 4 |           |
| DS920+       | DSM 7.2.1-69057 Update 3 |           |
| DS920+       | DSM 7.2.1-69057 Update 2 |           |
| DS920+       | DSM 7.2.1-69057 update 1 |           |
| DS920+       | DSM 7.2.1-69057          |           |
| DS920+       | DSM 7.2-64570 Update 1   |           |
| DS920+       | DSM 7.2-64561            |           |
| DS920+       | DSM 7.2-64216 Beta       |           |
| DS920+       | DSM 7.1.1-42962 Update 1 |           |
| DS918+       | DSM 7.2-64570 Update 3   |           |
| RS820+       | DSM 7.2-64570 Update 3   | M2D20     |
| DS720+       | DSM 7.2.1-69057 Update 4 |           |
| DS720+       | DSM 7.2.1-69057 Update 3 |           |
| DS720+       | DSM 7.2.1-69057 Update 2 |           |
| DS720+       | DSM 7.2.1-69057 Update 1 |           |
| DS720+       | DSM 7.2.1-69057          |           |
| DS720+       | DSM 7.2-64570 Update 3   |           |
| DS720+       | DSM 7.2-64570 Update 1   |           |
| DS720+       | DSM 7.2-64570            |           |
| DS720+       | DSM 7.2-64561            |           |
| DS720+       | DSM 7.2-64216 Beta       |           |
| DS420+       | DSM 7.2-64570 Update 1   |           |
| DS1819+      | DSM 7.2-64216 Beta       | M2D20     |
| DS1819+      | DSM 7.1.1                | M2D20     |
| DS1019+      | DSM 7.2.1-69057 Update 2 |           |
| DS1019+      | DSM 7.2-64561            |           |
| DS1019+      | DSM 7.1.1-42962 Update 4 |           |
| DS1618+      | DSM 7.1.1                | M2D18     |
| DS918+       | DSM 7.2.1-69057 Update 5 |           |
| DS918+       | DSM 7.2-64561            |           |
| DS918+       | DSM 7.1.1                |           |
| DS3617xs     | DSM 7.2-64570            | M2D20     |

</details>

### Важно

Если после обновления DSM ваши диски M.2 отображаются как неподдерживаемые, а пул носителей отображается как отсутствующий, а онлайн-сборка завершается сбоем, вам необходимо запустить сценарий <a href="https://github.com/ZwiReKsyno/Synology_HDD_SATA_NVMe"> Сценарий Synology_HDD_db должен запускаться после каждого обновления DSM.

### Скачать сценарий

1. Загрузите исходный код последней версии (zip) с https://github.com/007revad/Synology_M2_volume/releases
2. Сохраните загруженный zip-файл в папку на Synology.
3. Разархивируйте zip-файл.

### Запуск скрипта через SSH

[How to enable SSH and login to DSM via SSH](https://kb.synology.com/en-global/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)

```YAML
sudo -s /volume1/scripts/syno_create_m2_volume.sh
```
а лучший способ сделать это — настроить запланированное задание для запуска сценария при загрузке.

Примечание.: Вы можете настроить задачу расписания и оставить ее отключенной, чтобы она запускалась только тогда, когда вы выбираете задачу в планировщике задач и нажимаете кнопку «Выполнить».

Перейдите в «Панель управления» > «Планировщик заданий» > нажмите «Создать» > и выберите «Запускаемая задача» .
Выберите Пользовательский сценарий .
Введите имя задачи.
Выберите root в качестве пользователя (сценарий должен запускаться от имени root).
Выберите «Загрузка» в качестве события, запускающего задачу.
Оставьте галочку «Включить ».
Нажмите «Настройки задачи» .
При желании вы можете установить флажок «Отправлять сведения о запуске по электронной почте» и «Отправлять сведения о запуске только в случае аварийного завершения сценария», а затем ввести свой адрес электронной почты.
В поле Пользовательский скрипт введите путь к скрипту.
например, если вы сохранили сценарий в общую папку на томе 1 под названием «scripts», вы должны ввести:
Замените /volume1/scripts/ путем к расположению сценария. (/volume1/my scripts/syno_create_m2_volume.sh)
Нажмите ОК, чтобы сохранить настройки.

**Примечание:** Замените /volume1/scripts/ путем к расположению сценария.

### Поиск неисправностей

Если скрипт не запускается, проверьте следующее:

1. Если путь к скрипту содержит пробелы, вам необходимо заключить путь/имя скрипта в двойные кавычки:
   ```YAML
   sudo -s "/volume1/my scripts/syno_create_m2_volume.sh"
   ```
2. Убедитесь, что вы распаковали загруженный файл zip или rar и пытаетесь запустить файл syno_create_m2_volume.sh.
3. Установите файл syno_create_m2_volume.sh как исполняемый
   ```YAML
   sudo chmod +x "/volume1/scripts/syno_create_m2_volume.sh"
   ```

### Параметры:
```YAML
  -a, --all        List all M.2 drives even if detected as active
  -s, --steps      Show the steps to do after running this script
  -h, --help       Show this help message
  -v, --version    Show the script version
```

### Что делать после запуска скрипта

1. Создайте том, как обычно:
    - Выберите новый пул носителей > Создать > Создать том.
    - Установите выделенный размер
      - При необходимости введите описание тома. Будь креативным :)
    - Нажмите "Далее.
    - Выберите файловую систему (Btrfs или ext4) и нажмите «Далее».
    - При желании включите «Шифровать этот том» и нажмите «Далее»
      - Создайте пароль шифрования или введите существующий пароль шифрования 
    - Подтвердите свои настройки и нажмите «Применить», чтобы завершить создание тома M.2.
4. При желании включите и запланируйте TRIM:
    - Пул носителей > ... > Настройки > SSD TRIM    
    - **Примечание: DSM 7.1.1. не имеет настройки SSD TRIM для пулов хранения данных M.2**
    - **Примечание. В бета-версии DSM 7.2 нет настройки SSD TRIM для M.2 RAID 0 или RAID 5**

-----
### Как восстановить пул носителей NVMe или перейти на более крупные диски

- **Примечание. Требуется DSM 7.2 или более поздней версии**.

- **Восстановите NVMe RAID 1 во внутренних слотах M.2**.
- Деактивируйте сбойный диск NVMe.
- Выключите Synology.
- Замените деактивированный диск NVMe.
- Загрузите Synology.
- Запустите Synology_HDD_db .
- Откройте диспетчер хранилища.
- Нажмите «Восстановить сейчас» в пуле носителей M.2 и выберите неиспользуемый диск NVMe.

- **Замените диски NVMe RAID 1 во внутренних слотах M.2 на диски большего размера**.
- Деактивируйте 1 из дисков NVMe (если один из них вышел из строя, выберите его).
- Выключите Synology.
- Замените деактивированный диск NVMe диском NVMe большего размера.
- Загрузите Synology.
- Запустите Synology_HDD_db https://github.com/ZwiReKsyno/Synology_HDD_SATA_NVMe
- Откройте диспетчер хранилища.
- Нажмите «Восстановить сейчас» в пуле носителей M.2 и выберите неиспользуемый диск NVMe большего размера.
- Дождитесь окончания ремонта.
- Повторите шаги с 1 по 8 для дисков NVMe в пуле носителей.
- Измените размер тома, чтобы использовать все доступное пространство:
- Выберите том в диспетчере хранилища> нажмите ... > нажмите «Настройки»> нажмите «Макс»> нажмите «Сохранить».

- **Восстановление RAID через SSH**
- **Эти шаги относятся к DSM 6**.

- Сначала сделайте резервную копию ваших данных!

- Запустите cat /proc/mdstat, чтобы проверить имена ваших устройств: /dev/md#и /dev/sda#или /dev/sata#или/dev/nvme#

- Выполните следующие команды:

sudo synospace --stop-all-spaces

sudo syno_poweroff_task -d

sudo mdadm -Sf /dev/md4 # Замените md4 правильным номером md

sudo mdadm -AfR /dev/md4 /dev/nvme2 # Замените md4 правильным номером md и nvme2 правильным номером nvme

-----
### Снимки экрана DSM 7

<p align="center">Create SHR Storage Pool</p>
<p align="center"><img src="/images/create_shr_v2.png"></p>

<p align="center">Create Volume</p>
<p align="center"><img src="/images/create-volume1.png"></p>

<p align="center">Volume description</p>
<p align="center"><img src="/images/create-volume3.png"></p>

<p align="center">Allocate volume capacity</p>
<p align="center"><img src="/images/create-volume2.png"></p>

<p align="center">Select file system</p>
<p align="center"><img src="/images/create-volume4.png"></p>

<p align="center">Success!</p>
<p align="center"><img src="/images/create-volume5.png"></p>

<p align="center">Enable TRIM</p>
<p align="center"><img src="/images/create_m2_volume_enable_trim.png"></p>


