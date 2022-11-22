import subprocess
import time
import yadisk
import shutil
import pathlib


# Ввод токена и его проверка, установка таймера проверки процесса обсидиан
y = yadisk.YaDisk(token='*****')
print(f'Are token valid? {y.check_token()}')
checker = 10

# Цикл проверки процесса Obsidian.exe через tasklist subprocess
while True:
    lit = str(subprocess.getoutput('tasklist'))
    obs = lit.find('Obsidian.exe')

    # Обсидиан запущен, следующая проверка через checker секунд
    if obs != -1:
        print(f'Obsidian is running...Next check after {checker} seconds')
        time.sleep(checker)

    # Обсидиан выключен. По порядку:
    # 1) Нахождение предыдущего бэкапа и его удаление
    # 2) Архивирование нового бэкапа
    # 3) Удаление старого бэкапа с диска и закгрузка нового
    elif obs == -1:
        pathlib.Path('C:\\Crypter.zip').unlink()
        shutil.make_archive('Crypter', 'zip', 'D:\\Crypter')
        y.remove('Crypter.zip', permanently=True)
        y.upload('C:\\Crypter.zip', 'Crypter.zip')
        print('Obsidian is shutdown, all files are backup in YandexDrive, check Crypter.zip')
        break
