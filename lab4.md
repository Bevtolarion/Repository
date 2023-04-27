В-первую очередь я создал HTML файл, с базовым кодом и добавил в тело обычный JS скрипт, в котором просто вылазит окошко, которое надо подтвердить.
После этого, я в созданной заранее папке, где лежал этот файл, открыл консоль.
Туда я вписал: 

docker run -d nginx 

Создал контейнер с nginx образом
После чего я создал dockerfile, используя 
echo $null dockerfile
И
оттредактировал текст используя "Docker desktop", прописав туда 

FROM nginx
COPY index.html /usr/share/nginx/html
COPY style.css /usr/share/nginx/html
COPY script.js /usr/share/nginx/html
После этого, я запустил сбор образа состоящего из nginx и index.html 

docker build . -t localhost:5000/nginx:0.0.1

Через "docker desktop" проверил рабочий ли контейнер, на всякий случай

Ввёл запуск образа docker run -itd -p 8011:80 --name nginx-dock localhost:5000/nginx:0.0.1

И перёшёл на страницу через http://localhost:8011/

Так-же перенёс потом докерфайл через 
docker build -f /Users/Win10Pro/Desktop/OS/Dockerfile 
в другую папку, где запустил его позже.  
