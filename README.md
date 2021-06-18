STEPS:

- настройка webhook для github
	В GitHub в репозитории проекта в разделе webhooks
	добавляем url до нашего Jinkins и в конце /github-webhook/
	( например http://exapmle.com/github-webhook/ )
	тип json, secret оставляем пока пустым (нужно глянуть как настроить в Jenkins скорее всего нужен https)
	таким образом при push будет срабатывать webhook,который будет дёргать jenkins-agent (раннер),
	который выполняет сценарий из Jenkinsfile

- настройка доступа к приватному репозиторию 'git@github.com:github-devops/jenkinsfile.git':
	доступ организовал через ssh ключ
	сгенерировал новый ключ через ssh-keygen, затем
	на github в репозиторий проекта добавил публичный, в jenkins - приватный

- настройка Node для агента (раннера) Jenkins
	1. предварительно установить java на целевом (wordpress) сервере.
	Создаём новую ноду в Jenkins, используя тип agent
	далее генерится инструкция в новой ноде по запуску agent на 
	целевом сервере. На целевом сервере пока запускаю в screen, но лучше наверное оформить в systemctl, 
	либо в docker контейнер
	2. настраиваем через ssh (на целевом сервере должен быть установлен java) 
