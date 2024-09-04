# CLI Cheat Sheet (Referências rápidas de Linha de Comando)

### Atalhos de teclado do Linux

- **`Ctrl+Alt+T`**: Abrir terminal a partir da interface gráfica do Ubuntu.
- **`Ctrl+C`**: é usado para matar um processo com o sinal SIGINT , em outras palavras, é um kill educado.
- **`Ctrl+Z`**: é usado para suspender um processo enviando a ele o sinal SIGTSTP , que é como um sinal de suspensão, que pode ser desfeito e o processo pode ser retomado novamente.
- **`Ctrl+D`**: sai da sessão atual, semelhante a sair.
- **`Ctrl+R`**: digite para abrir um comando recente
- **`Ctrl+W`**: apaga uma palavra na linha atual
- **`Ctrl+U`**: apaga a linha inteira

### Comandos auxiliares

- **`history`**: Pesquisa na relação dos ultimos comandos do usuário corrente
- **`!!`**: repete o último comando
- **`exit`**: sai da sessão atual
- **`history | grep "command looking for"  | tail -n 10`**: Concatenação de comandos, lista os ultimos 10 comandos a partir do comando pesquisado

---
## Sistema

### Informações do sistema
- **`uname -a`** : Exibe todas as informações do sistema.
- **`hostnamectl`** : Mostra o nome do host atual e detalhes relacionados.
- **`lscpu`** : Lista informações de arquitetura da CPU.
- **`timedatectl status`** : Mostra a hora do sistema.

### Monitoramento e gerenciamento do sistema
- **`top`** : Exibe processos do sistema em tempo real.
- **`htop`** : Um visualizador de processo interativo (precisa de instalação).
- **`btop`** : Um visualizador de processo interativo, mais recente e de melhor visualização (precisa de instalação: `snap install btop` ).
- **`df -h`** : Mostra o uso do disco em um formato legível por humanos.
- **`du -h --max-depth=1`**: Mostra o tamanho ocupado pelos diretório, com apenas 1 nível de detalhamento, legível para humanos
- **`free -m`** : Exibe memória livre e usada em MB.
- **`kill <id do processo>`** : Encerra um processo.

### Executando comandos
- **`[comando] &`** : Executa o comando em segundo plano.
- **`jobs`** : Exibe os comandos em segundo plano.
- **`fg <número do comando>`** : Traz o comando para o primeiro plano.

### Gerenciamento de serviços
- **`sudo systemctl start <service>`** : Inicia um serviço.
- **`sudo systemctl stop <service>`** : Interrompe um serviço
- **`sudo systemctl status <service>`** : Verifica o status de um serviço.
- **`sudo systemctl reload <service>`** : Recarrega a configuração de um serviço sem interromper sua operação.
- **`journalctl -f`** : Segue o diário, mostrando novas mensagens de log em tempo real.
- **`journalctl -u <unit_name>`** : Exibe logs para uma unidade systemd específica.

### Trabalhos cron e agendamento
- **`crontab -e`** : Edita trabalhos cron para o usuário atual.
- **`crontab -l`** : Lista trabalhos cron para o usuário atual.



---
## Files

### Gerenciamento de arquivos
- **`ls`** : Lista arquivos e diretórios.
- **`touch <nome do arquivo>`** : Cria um arquivo vazio ou atualiza a data do último acesso.
- **`cp <origem> <destino>`** : Copia arquivos da origem para o destino.
- **`mv <origem> <destino>`** : Move arquivos ou os renomeia.
- **`rm <nome do arquivo>`** : Exclui um arquivo.


### Navegação de diretório
- **`pwd`** : Exibe o caminho do diretório atual.
- **`cd <diretório>`** : Altera o diretório atual.
- **`mkdir <nome do diretório>`** : Cria um novo diretório.

### Permissões e propriedade de arquivos
- **`chmod [who][+/-][permissions] <file>`** : Altera as permissões de arquivo.
- **`chmod u+x <file>`** : Torna um arquivo executável pelo seu dono.
- **`chown [usuário]:[grupo] <file>`** : Altera o dono e o grupo do arquivo.

#### File Permissions
- **`chmod <octal> <file>`** – altere as permissões do arquivo para <octal>, que pode ser encontrado separadamente para usuário, grupo e mundo adicionando:
  - `4` – read (`r`)
  - `2` – write (`w`)
  - `1` – execute (`x`)
  - Onde o número do grupo significa:
    - `7` = `rwx` = (4+2+1)
    - `6` = `rw-` = (4+2)
    - `5` = `r-x` = (4+1)
    - `4` = `r--` = (4)
    - `3` = `-wx` = (2+1)
    - `2` = `-w-` = (2)
    - `1` = `--x` = (1)
  - E o conjunto gera:
    - `-rwxrw-r-- ` : Conjunto sendo:
    - `| |  |  |  `
    - `| |  |  +--> [r--]`: Outros usuários têm permissão apenas de leitura.
    - `| |  +-----> [rw-]`: O grupo tem permissão apenas de leitura e escrita.
    - `| +-------> [rw-]`: O usuário (proprietário) tem permissão completa `[rwx]`
    - `+----------> [-]`: Primeira posição indica o tipo de arquivo, sendo: `[-]` Arquivo regular. `[d]` diretório. `[l]` link simbólico.

- Examples:
  - `chmod 777` – read, write, execute for all
  - `chmod 755` – `rwx` for owner, `rx` for group and world

### Pesquisando e encontrando
- **`find [diretório] -name <padrão_de_pesquisa>`** : Encontra arquivos e diretórios.
- **`grep <padrão_de_pesquisa> <file>`** : Procura um padrão em arquivos.

### Arquivamento e compactação
- **`tar -czvf <nome.tar.gz> [arquivos]`** : Compacta arquivos em um arquivo tar.gz.
- **`tar -xvf <nome.tar.[gz|bz|xz]> [destino]`** : Extrai um arquivo tar compactado.
- **`7z a <novo_arquivo_compactado>.7z <nome_arquivo_a_compactar,nome_arquivo_a_compactar>`** : Compacta em 7z
- **`7z x <novo_arquivo_compactado>.7z`** : Descompacta o arquivo 7z

### Edição e processamento de texto
- **`nano [arquivo]`** : Abre um arquivo no editor de texto Nano.
- **`cat <file>`** : Exibe o conteúdo de um arquivo.
- **`less <file>`** : Exibe o conteúdo paginado de um arquivo.
- **`head <file>`** : Mostra as primeiras linhas de um arquivo.
- **`tail <file>`** : Mostra as últimas linhas de um arquivo.
- **`awk ‘{print}’ [file]`** : Imprime cada linha em um arquivo.



---
## Pacotes

### Gerenciamento de pacotes (APT)
- **`sudo apt install <pacote>`** : Instala um pacote.
- **`sudo apt install -f –reinstall <pacote>`** : Reinstala um pacote quebrado.
- **`apt search <pacote>`** : Pesquisa por pacotes APT.
- **`apt-cache policy <pacote>`** : Lista as versões de pacotes disponíveis.
- **`sudo apt update`** : Atualiza as listas de pacotes.
- **`sudo apt upgrade`** : Atualiza todos os pacotes atualizáveis.
- **`sudo apt remove <pacote>`** : Remove um pacote.
- **`sudo apt purge <pacote>`** : Remove um pacote e todos os seus arquivos de configuração.

### Gerenciamento de pacotes (Snap)
- **`snap find <pacote>`** : Pesquisa por pacotes Snap.
- **`sudo snap install <snap_name>`** : Instala um pacote Snap.
- **`sudo snap remove <snap_name>`** : Remove um pacote Snap.
- **`sudo snap refresh`** : Atualiza todos os pacotes Snap instalados.
- **`snap list`** : Lista todos os pacotes Snap instalados.
- **`snap info <snap_name>`** : Exibe informações sobre um pacote Snap.



---
## Usuários e grupos

### Gerenciamento de usuários
- **`w`** : Mostra quais usuários estão logados.
- **`sudo adduser <username>`** : Cria um novo usuário.
- **`sudo deluser <username>`** : Exclui um usuário.
- **`sudo passwd <username>`** : Define ou altera a senha de um usuário.
- **`su <username>`** : Troca de usuário.
- **`sudo passwd -l <nome de usuário>`** : Bloqueia uma conta de usuário.
- **`sudo passwd -u <nome de usuário>`** : Desbloqueia uma senha de usuário.
- **`Sudo change <nome de usuário>`** : Define a data de expiração da senha do usuário.

### Gerenciamento de grupo
- **`id [nome de usuário]`** : Exibe IDs de usuário e grupo.
- **`groups [nome de usuário]`** : Mostra os grupos aos quais um usuário pertence.
- **`sudo addgroup <nome de grupo>`** : Cria um novo grupo.
- **`sudo delgroup <nome de grupo>`** : Exclui um grupo.



---
## Rede

### Rede
- **`ip addr show`** : Exibe interfaces de rede e endereços IP.
- **`ip -s link`** : Mostra estatísticas de rede.
- **`ss -l`** : Mostra soquetes de escuta.
- **`ping <host>`** : Faz ping em um host e exibe resultados.

### Configuração do Netplan (leia mais em netplan.io)
- **`cat /etc/netplan/*.yaml`** : Exibe a configuração atual do Netplan.
- **`sudo netplan try`** : Testa uma nova configuração por um período de tempo definido.
- **`sudo netplan apply`** : Aplica a configuração atual do Netplan.

### Gerenciamento de firewall
- **`sudo ufw status`** : Exibe o status do firewall.
- **`sudo ufw enable`** : Habilita o firewall.
- **`sudo ufw disable`** : Desativa o firewall.
- **`sudo ufw allow <porta/serviço>`** : Permite tráfego em uma porta ou serviço específico.
- **`sudo ufw deny <porta/serviço>`** : Nega tráfego em uma porta ou serviço específico.
- **`sudo ufw delete allow/deny <porta/serviço>`** : Exclui uma regra existente.

### SSH e acesso remoto
- **`ssh <usuário@host>`** : Conecta-se a um host remoto via SSH.
- **`scp <origem> <usuário@host>:<destino>`** : Copia arquivos com segurança entre hosts.

### Gerenciamento de firewall
- **`sudo ufw status`** : Exibe o status do firewall.
- **`sudo ufw enable`** : Habilita o firewall.
- **`sudo ufw disable`** : Desativa o firewall.
- **`sudo ufw allow <porta/serviço>`** : Permite tráfego em uma porta ou serviço específico.
- **`sudo ufw deny <porta/serviço>`** : Nega tráfego em uma porta ou serviço específico.
- **`sudo ufw delete allow/deny <porta/serviço>`** : Exclui uma regra existente.

### Comandos extras
- **`ping <host>`**: ping host and output results
- **`whois <domain>`**: get whois information for domain
- **`dig <domain>`**: get DNS information for domain
- **`dig -x <host>`**: reverse lookup host
- **`wget <file>`**: download file
- **`wget -c <file>`**: continue a stopped download


#### References
Ubuntu CLI and Personal knowledge


