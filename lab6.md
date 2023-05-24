Первым делом установил Node.js с официального сайта  (https://nodejs.org)
Установил Vue CLI - инструмент командной строки, для настройки и управления проекта на Vue.js, установку делал через командную строку используя этот код 

npm install -g @vue/cli

После установок создал новый проект в папке под названием lab6, и там ввёл vue create lab6. Эта команда сделала новую директорию с именем lab6.
Перехожу в директорию моего проекта и ввожу npm run serve для запуска локального сервера разработки. 
Добавил в vue.js этот код

module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:8000',
        changeOrigin: true
      }
    }
  }
}

И установил конфигурации 

server {
    listen 8000;
    
    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

Создал конфигурационный сервер nginx 
Активировал конфигурацию nginx 
sudo ln -s /etc/nginx/sites-available/lab6 /etc/nginx/sites-enabled/

Перезапустил Nginx, чтобы конфигурация подгрузилась