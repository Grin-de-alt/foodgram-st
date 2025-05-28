Находясь в папке infra, выполните команду docker-compose up. При выполнении этой команды контейнер frontend, описанный в docker-compose.yml, подготовит файлы, необходимые для работы фронтенд-приложения, а затем прекратит свою работу.

По адресу http://localhost изучите фронтенд веб-приложения, а по адресу http://localhost/api/docs/ — спецификацию API.

## Сайт расположен по адресу: https://foodgramdgg.ddnsking.com
# Запуск API:
- Склонируйте репозиторий:
```bash 
git clone ...
```    
- Установите и активируйте виртуальное окружение:
```bash
python -m venv venv 
```  
``` bash 
source venv/Scripts/activate 
``` 
- Установите зависимости из файла requirements.txt:
``` bash 
pip install -r requirements.txt 
```
- Примените миграции:
``` bash
python manage.py migrate
```
- Запустите проект:
```bash
python manage.py runserver
```
### Документация доступна по адресу:
```
http://127.0.0.1/api/docs/
```

# Запуск проекта в контейнерах
- Перейти в директорию /infra и выполнить следующие команды:
```
docker-compose build
```
```
docker-compose up -d
```
```
docker-compose up
```
- Применить миграции:
```
docker compose exec backend python manage.py makemigrations
```
```
docker compose exec backend python manage.py migrate
```
- Собрать статику:
```
docker-compose exec python manage.py collectstatic --no-input 
```
- Загрузить ингредиенты:
```
docker-compose exec backend python manage.py load_csv
```
- Создать суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
