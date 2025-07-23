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

- **LINK ÚTIL**
  https://www.devmedia.com.br/comandos-importantes-linux/23893


## ALIAS
- **Na root execute:** `sudo nano .bash_aliases`
- **Utilize a estrutura:** `alias §Nome do alias§='§comandos do alias§'`


## COMANDO 

- **FIND**
  - **Documentação oficial**
    - https://www.gnu.org/software/findutils/manual/find.html
    - https://www.gnu.org/software/findutils/manual/find.pdf

  - **Base**
    - `find` + `[diretorio de busca, se for onde está use o "."]` + `[Parâmetros]`
  
  - **Parâmetros:**
    - Sem parâmetros o comando retorna TUDO
    - `-empty`: filtra apenas os itens vazios
    - `-delete`: apaga todos os retornos
    - `-not`: Nega o próximo parametro
    - `-exec`: Expecifica que para cada retorno deverá executar a proxima função
    - `execdir`: Expecifica que para cada retorno de
     diretorio executa a proxima função
    - `-type [d, f, l, c, b, p, s]`: filtra a busca apenas por:
      - `f` Arquivos regulares
      - `d` Diretórios
      - `l` Link simbólicos
      - `c` Dispositivo de caracteres
      - `b` Dipositivo de bloco
      - `p` Pipe nomeado
      - `s` Soquete
    - `-name ["nm"]`: Passa um nome ["mn"] como filtro
    - `-path ["./"]`: Passa um nome ["./"] como filtro no caminho  
    - `-mtime [n]`: Filtra tudo que foi modificado nos ultimos "n" dias
    - `-newer [nome.txt]`: Filtra por tudo que é mais novo que um arquivo [nome.txt]
    - `-size [+50M, -1G]`: filtra por tamanho, por exemplo, tudo que tenha mais de 50 mega [+50M] ou menos de 1 giga [-1G]
    - `-perm [n]`: filtra por tudo que tenha a permissão [n]
    - `-maxdepth [n]`: especifica a profuncidade méxima de subdiretórios em [n].
    - `-mindepth [n]`: especifica a profindidade minima de subtiretórios em [n].
    - `-user [usuario]`: filtra a busca apenas por arquivos pertencentes ao usuário [usuraio]
    - ``:
- **WC**
  - **Documentação útil**
    - https://guialinux.uniriotec.br/wc/

  - **Base**
    - `wc` + `método`
    - Deve receber um conjunto de dados

  - **Parâmetros**
    - Sem parâmetros o comando retornao:
      - n de Linhas
      - n de palanhas
      - Tamanho de bytes
      - Nome do arquivo
    - `-c`: Conta os bytes
    - `-l`: Conta linhas
    - `-L`: Mostra a linha mais longa
    - `-m`: Conta os caracteres
    - `-w`: Conta as palavras

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
