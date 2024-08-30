# CLI cheat sheet (Referências rápidas de Linha de Comando)

---
## Sistema

### Informações do sistema
- **`uname -a``** : Exibe todas as informações do sistema.
- **`hostnamectl`** : Mostra o nome do host atual e detalhes relacionados.
- **`lscpu`** : Lista informações de arquitetura da CPU.
- **`timedatectl status`** : Mostra a hora do sistema.

### Monitoramento e gerenciamento do sistema
- **`top`** : Exibe processos do sistema em tempo real.
- **`htop`** : Um visualizador de processo interativo (precisa de instalação).
- **`btop`** : Um visualizador de processo interativo, mais recente e de melhor visualização (precisa de instalação: `snap install btop` ).
- **`df -h`** : Mostra o uso do disco em um formato legível por humanos.
- **`free -m`** : Exibe memória livre e usada em MB.
- **`kill <id do processo>`** : Encerra um processo.

### Monitoramento e gerenciamento do sistema
- **`top`** : Exibe processos do sistema em tempo real.
- **`htop`** : Um visualizador de processo interativo (precisa de instalação).
- **`df -h`** : Mostra o uso do disco em um formato legível por humanos.
- **`free -m`** : Exibe a memória livre e usada em MB.
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

### Pesquisando e encontrando
- **`find [diretório] -name <padrão_de_pesquisa>`** : Encontra arquivos e diretórios.
- **`grep <padrão_de_pesquisa> <file>`** : Procura um padrão em arquivos.

### Arquivamento e compactação
- **`tar -czvf <nome.tar.gz> [arquivos]`** : Compacta arquivos em um arquivo tar.gz.
- **`tar -xvf <nome.tar.[gz|bz|xz]> [destino]`** : Extrai um arquivo tar compactado.

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

### SSH e acesso remoto
- **`ssh <usuário@host>`** : Conecta-se a um host remoto via SSH.
- **`scp <origem> <usuário@host>:<destino>`** : Copia arquivos com segurança entre hosts

