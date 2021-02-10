### for_GIt_in_sky

Данный ansible playbook выполняет следующие действия
  1. роль initial_settings 
  * устанавливает дополнительные  пакеты (zsh-5.4*  wget-1.19.4* unzip nginx-1.14.* letsencrypt  )  tag: install
  * меняет настройки файла sysctl.conf ( параметры net.core.somaxconn и fs.file-max) tag: sysctl
  * добовляет пользователя admin (включает его в группу sudo, устанавливает пароль, добавляет два ssh_rsa_pub  ключа) tag: add_user
  2. роль  create_TLS_key tag: TLS
  * делает проверку на наличие ключа для ssl
  * получает новый ключь (если его небыло)
  * описывает новое правило в crontab  (для автоматического продления ключа)
  3. роль add_virthost_file
  * скачиваем файл со страницей по умолчанию из git  репозитория (можно подумать над копированием архива) tag: copying_page
  * копируем на целевой сервер файл virthost  с настройками сервера  tag: virthost
  * определяем файл virthost как настройки поумолчанию tag: virthost
