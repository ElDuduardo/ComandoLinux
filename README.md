# ComandosLinux

> Alguns comandos do terminal linux que uso e descobri que podem ser úteis no dia a dia.

## COMANDOS COMUNS
- **Básicos**
  - `sudo`: executa como adm
  - `cd`: se movimenta pelos diretórios
  - `ls`: lista o conteúdo de um diretório
  - `apt-get`: gerenciador de pacotes
  - `apt`: "Advanced Package Tool", apt-get atualizado
  - `--help`: parte de algumas funções, exibe um texto de ajuda
- **OUTROS**
  - `awk`: Realiza ações em linhas baseada na coluna
  - `find`: busca baseada em critérios
  - `curl`: envia e recebe arquivo web via endereço
  - `wget`: recebe arquivos da web de maneira não interativa
  - `du`: "Drive Usage" avalia o tamanho de diretórios e arquivos no disco
  - `ssh`: "Secure SHell" possibilita acesso remoto
  - `>`: Joga o resultado de uma execução na outra
  - `touch`: Cria um novo arquivo
  - `rename`: Renomeia os arquivos baseados em critérios

## BUSCAR ARQUIVO PELO NOME
`sudo find / -name <arquivo> 2>/dev/null`

## LISTA AS PASTAS VAZIAS E:
- **Retorna**: `find . -type d -empty`
- **Apaga**: `find . -type d -empty -delete`

## BUSCAR TODOS E:
- **Coloca os diretórios em um txt**: `find "INOVA - Unioeste INOVA 2023" -type d > Pastas.txt`
- **Conta quantas pastas há**: `find . -type d 2>/dev/null | wc -l`
- **Lista o tamanho dos diretórios atuais.**: `du -sh ./*/ > Arquivo.txt`
- **Lista todos os diretórios com os tamanhos**: `du -sh ./*/`
- **Substitui no nome o termo "<antigo>" pelo "<novo>"**: `find . -depth -name '*<antigo>*' -execdir bash -c 'for f; do mv -v -- "$f" "${f//<antigo>/<novo>}"; done' _ {} +`

## LISTA AS PASTAS COM MENOS DE 1kb
- **Retorna a lista falando q vai apagar**: `find . -type d -name "15_AGEUNI" -exec du -s {} + | awk '$1 < 1 {print "Would remove: "$2}'`
- **Apaga as pastas**: `find . -type d -exec du {} + | awk '$1 < 1 {print "Would remove: "$2}'`

## DOCKER
- **Criar**
  - `docker run --name <nome-docker> -p <porta>:<porta> -e POSTGRES_PASSWORD=<senha> -d postgres:14`
  - `sudo docker exec -it <nome-docker> psql -U postgres`
  - `CREATE USER <nome-usario> WITH PASSWORD ‘<senha>’;`
  - `CREATE DATABASE "berimbau" OWNER <nome-usario>;`
  - `GRANT ALL PRIVILEGES ON DATABASE berimbau TO <nome-usario>;`
  - `docker exec -it <nome-docker> psql -U <nome-usario> -d berimbau`
- **Iniciar**: `sudo docker start <nome-docker>`
- **Parar**: `sudo Docker kill <nome-docker>`
