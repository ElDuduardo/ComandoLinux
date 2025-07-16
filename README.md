# ComandosLinux

> Alguns comandos do terminal linux que uso e descobri que podem ser úteis no dia a dia.
> Como presuposto interprete "§" como inicaidores e finalizadores dos termos que **VOCÊ** deve editar.

## COMANDOS COMUNS
- **Básicos**
  - `sudo`: executa como adm
  - `cd`: entra e sair das pastas
  - `ls`: lista o conteúdo de um diretório
  - `apt-get`: gerenciador de pacotes
  - `apt`: "Advanced Package Tool", apt-get atualizado
  - `clear`: limpa o que ta escrito no terminal
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
  - `mv`: renomeia ou movimenta um arquivo

## ALIAS
- **Na root execute:** `sudo nano .bash_alises`
- **Utilize a estrutura:** `alias §Nome do alias§='§comandos do alias§'`

## BUSCAR ARQUIVO PELO NOME
`sudo find . -name §Nome do Arquivo§ 2>/dev/null`

## LISTA AS PASTAS VAZIAS E:
- **Retorna**: `find . -type d -empty`
- **Apaga**: `find . -type d -empty -delete`

## BUSCAR TODOS E:
- **Coloca os diretórios em um txt**: `find "*§Nome da Pasta§*" -type d > Pastas.txt`
- **Conta quantas pastas há**: `find . -type d | wc -l`
- **Lista o tamanho dos diretórios atuais.**: `du -sh ./*/ > Arquivo.txt`
- **Lista todos os diretórios com os tamanhos**: `du -sh ./*/`
- **Substitui no nome o termo "<antigo>" pelo "<novo>"**: `find . -depth -name '*§Termo para trocar§*' -execdir bash -c 'for f; do mv -v -- "$f" "${f//§Termo para trocar§/§Novo Termo§}"; done' _ {} +`

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
