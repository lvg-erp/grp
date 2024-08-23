Слои:
    Transport - обработка(роутинг запросов) gRPC
        App - слой запуска и остановки приложения
    Service - бизнес логика(например авторизация, воркеры)
    Data - общение с БД
#################################################################
Для корректной отправки на ГИТ 
необходимо сгенерить мод файл
так
go mod init github.com/lvg-erp/grpc


Директория protos
Для генерации протофайла устанавливаем protoc
https://grpc.io/docs/protoc-installation/
из терминала
    $ apt install -y protobuf-compiler
    $ protoc --version
в проекте
    go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
    go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
в проекте генерим папки
    /Project/go/grpc/protos$ mkdir -p gen/go
    генерим файлы
    /Project/go/grpc/protos$ 
    команда: protoc -I proto proto/sso/sso.proto --go_out=./gen/go/ --go_opt=paths=source_relative --go-grpc_out=./gen/go --go-grpc_opt=paths=source_relative
на неустановленные пакеты не обращаем внимания, в процессе установим.....

создаем таск файл.... и через него гененрим все нужные файлы
не забываем прописывать переменные окружения

export PATH="$PATH:$(go env GOPATH)/bin"

task generate
поднимаем версию через 
    git tag v0.0.1
    git push origin v0.0.1
{проработать для закрытого репозитория}
/Project/go/grpc/protos$ go get github.com/ilyakaznacheev/cleanenv

[//]: # (ПЕРЕХОДИМ в директорию sso &#40;но прежде проект нужно опубликовать на гите&#41;)

[//]: # ()
[//]: # (/Project/go/grpc/protos$ go get github.com/ilyakaznacheev/cleanenv)

[//]: # ()
[//]: # (установка конфигурационного пути)

[//]: # (CONFIG_PATH=./path/to/config/file.yaml sso)

[//]: # (or)

[//]: # (sso --config=./path...)

[//]: # ()
[//]: # (создаем mod)

[//]: # (тянем версию прота)

[//]: # (/Project/go/grpc/sso$ go get github.com/lvg-erp/grpc/protos)

    