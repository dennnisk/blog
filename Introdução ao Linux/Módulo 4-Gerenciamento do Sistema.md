# Módulo 4: Gerenciamento do Sistema


## Usuários e Grupos no Linux

O Linux é um sistema operacional multiusuário, o que significa que ele pode ser utilizado por vários usuários simultaneamente, cada um com suas próprias permissões e configurações. Para gerenciar esses usuários de forma eficiente, o Linux utiliza o conceito de **usuários** e **grupos**, que permite controlar o acesso a arquivos, diretórios e recursos do sistema.

### 1. **O que são Usuários?**
Um **usuário** no Linux é uma identidade associada a uma pessoa ou a um processo, que tem permissões para acessar o sistema. Cada usuário possui um **nome de usuário** (login), um **UID** (User ID), e um **diretório home**, onde ficam armazenados seus arquivos pessoais. Além disso, cada usuário tem um conjunto de permissões e pertences a um ou mais grupos, que ajudam a definir o que ele pode ou não fazer no sistema.

#### Tipos de Usuários:
- **Root**: O usuário **root** é o administrador do sistema e tem permissões para realizar qualquer ação, como alterar arquivos de sistema, instalar softwares e configurar o sistema. O UID do root é sempre `0`.
- **Usuários comuns**: São os usuários criados para pessoas que utilizarão o sistema no dia a dia, com permissões limitadas para evitar que alterem ou danifiquem o sistema.
- **Usuários de sistema**: São contas criadas pelo sistema para executar serviços e processos. Esses usuários não fazem login diretamente e possuem permissões específicas para as tarefas que realizam.

### 2. **O que são Grupos?**
Os **grupos** no Linux são uma forma de organizar e gerenciar as permissões dos usuários. Um grupo é uma coleção de usuários que compartilham permissões de acesso a arquivos, diretórios e outros recursos do sistema. Cada usuário pode pertencer a um ou mais grupos, o que facilita a administração de permissões para equipes ou conjuntos de usuários.

#### Tipos de Grupos:
- **Grupo primário**: Cada usuário pertence a um grupo primário. Normalmente, esse grupo tem o mesmo nome que o usuário e é o grupo ao qual pertencem os arquivos criados pelo usuário.
- **Grupos suplementares**: Um usuário também pode pertencer a outros grupos adicionais, que lhe concedem permissões extras em certos arquivos e diretórios.

### 3. **Gerenciamento de Usuários**

#### 3.1. **Adicionar um novo usuário**
Para criar um novo usuário, utiliza-se o comando `adduser`, que automaticamente cria um diretório home e solicita a configuração de uma senha para o usuário.

#### Comando:
```
sudo adduser [nome_do_usuário]
```

#### Exemplo:
- Para criar um novo usuário chamado `joao`:
  ```
  sudo adduser joao
  ```

O comando solicitará informações como senha e nome completo, e criará automaticamente o diretório `/home/joao`.

#### 3.2. **Remover um usuário**
Para remover um usuário do sistema, utiliza-se o comando `deluser`. Ele remove o usuário e, se necessário, também pode remover o diretório home associado a ele.

#### Comando:
```
sudo deluser [nome_do_usuário]
```

#### Exemplo:
- Para remover o usuário `joao`:
  ```
  sudo deluser joao
  ```

#### 3.3. **Alterar as informações de um usuário**
O comando `usermod` permite modificar as informações de um usuário existente, como alterar o grupo principal, mudar o shell padrão, ou adicionar/remover o usuário de grupos adicionais.

#### Comando:
```
sudo usermod [opções] [nome_do_usuário]
```

#### Exemplo:
- Para adicionar o usuário `joao` ao grupo `sudo` (concedendo-lhe permissões administrativas):
  ```
  sudo usermod -aG sudo joao
  ```

### 4. **Gerenciamento de Grupos**

#### 4.1. **Criar um novo grupo**
Para criar um novo grupo, utiliza-se o comando `addgroup`.

#### Comando:
```
sudo addgroup [nome_do_grupo]
```

#### Exemplo:
- Para criar um grupo chamado `desenvolvedores`:
  ```
  sudo addgroup desenvolvedores
  ```

#### 4.2. **Adicionar um usuário a um grupo**
Para adicionar um usuário a um grupo existente, utiliza-se o comando `usermod` com a opção `-aG` (append to group).

#### Comando:
```
sudo usermod -aG [nome_do_grupo] [nome_do_usuário]
```

#### Exemplo:
- Para adicionar o usuário `joao` ao grupo `desenvolvedores`:
  ```
  sudo usermod -aG desenvolvedores joao
  ```

#### 4.3. **Remover um usuário de um grupo**
Para remover um usuário de um grupo, utiliza-se o comando `gpasswd`.

#### Comando:
```
sudo gpasswd -d [nome_do_usuário] [nome_do_grupo]
```

#### Exemplo:
- Para remover o usuário `joao` do grupo `desenvolvedores`:
  ```
  sudo gpasswd -d joao desenvolvedores
  ```

### 5. **Verificando Usuários e Grupos**

#### 5.1. **Verificar os grupos de um usuário**
Para listar todos os grupos aos quais um usuário pertence, utiliza-se o comando `groups`.

#### Comando:
```
groups [nome_do_usuário]
```

#### Exemplo:
- Para verificar os grupos aos quais o usuário `joao` pertence:
  ```
  groups joao
  ```

#### 5.2. **Listar todos os usuários do sistema**
Para listar todos os usuários do sistema, você pode visualizar o arquivo `/etc/passwd`, que contém as informações de login.

#### Comando:
```
cat /etc/passwd
```

Este arquivo contém várias informações, incluindo o nome de usuário, o diretório home, e o shell padrão de cada usuário.

#### 5.3. **Listar todos os grupos do sistema**
Para listar todos os grupos existentes no sistema, você pode visualizar o arquivo `/etc/group`.

#### Comando:
```
cat /etc/group
```

### 6. **Permissões de Arquivos e Grupos**

No Linux, cada arquivo e diretório tem permissões associadas a três categorias:
- **Usuário (u)**: O proprietário do arquivo.
- **Grupo (g)**: O grupo associado ao arquivo.
- **Outros (o)**: Todos os outros usuários que não são nem o dono nem membros do grupo.

As permissões podem ser de leitura (r), escrita (w), e execução (x). Você pode visualizar as permissões com o comando `ls -l`, e modificá-las com o comando `chmod`.

#### Exemplo:
- Para conceder permissão de leitura e escrita para o grupo em um arquivo `documento.txt`:
  ```
  chmod g+rw documento.txt
  ```

### Conclusão

O gerenciamento de **usuários e grupos** no Linux é fundamental para garantir a segurança e a organização do sistema, especialmente em ambientes multiusuário. Com esses comandos, você pode criar e remover usuários e grupos, alterar suas permissões e organizar o acesso a arquivos e recursos de forma eficiente.




---
## Tarefas Agendadas no Linux

O Linux oferece poderosas ferramentas para automatizar tarefas, permitindo que processos sejam executados automaticamente em horários ou intervalos específicos. Essa automação é realizada principalmente através de dois mecanismos: **cron** e **at**. Com essas ferramentas, você pode agendar tarefas recorrentes (como backups diários ou atualizações) ou agendar tarefas para serem executadas uma única vez em um momento futuro.

### 1. **Introdução ao `cron`**

O **cron** é um serviço do sistema Linux utilizado para agendar tarefas repetitivas. Ele executa comandos ou scripts automaticamente em horários ou intervalos específicos, definidos pelo usuário. As tarefas agendadas pelo cron são registradas em um arquivo chamado **crontab**.

#### Estrutura do Crontab

O **crontab** (cron table) é o arquivo de configuração onde você define as tarefas agendadas. Cada linha do crontab representa uma tarefa e segue uma estrutura de cinco campos de tempo, seguidos pelo comando a ser executado:

```
* * * * * comando
- - - - -
| | | | |
| | | | +--- Dia da semana (0 - 7) (0 ou 7 = domingo)
| | | +----- Mês (1 - 12)
| | +------- Dia do mês (1 - 31)
| +--------- Hora (0 - 23)
+----------- Minuto (0 - 59)
```

#### Comandos Básicos do `cron`

- **Editar o crontab do usuário atual**:
  ```
  crontab -e
  ```
  Esse comando abre o crontab no editor de texto padrão, onde você pode adicionar ou editar tarefas agendadas.

- **Listar tarefas agendadas do usuário atual**:
  ```
  crontab -l
  ```
  Exibe todas as tarefas agendadas no crontab do usuário atual.

- **Remover o crontab do usuário atual**:
  ```
  crontab -r
  ```
  Remove todas as tarefas agendadas do crontab do usuário atual.

#### Exemplo de Agendamento com `cron`:

1. **Agendar um backup diário**:
   - Para agendar um backup às 2h da manhã todos os dias:
     ```
     0 2 * * * /home/usuario/scripts/backup.sh
     ```
     Esse comando executa o script `backup.sh` localizado em `/home/usuario/scripts/` todos os dias às 2h da manhã.

2. **Executar uma tarefa a cada 15 minutos**:
   - Para executar um comando a cada 15 minutos:
     ```
     */15 * * * * /home/usuario/scripts/check-disk.sh
     ```
     Esse comando executa o script `check-disk.sh` a cada 15 minutos.

3. **Limpar o diretório temporário todo domingo à meia-noite**:
   - Para agendar uma limpeza do diretório `/tmp` todo domingo à meia-noite:
     ```
     0 0 * * 0 rm -rf /tmp/*
     ```
     Esse comando remove todos os arquivos do diretório `/tmp` às 00:00 (meia-noite) de cada domingo.

#### Caracteres Especiais no Crontab:
- **`*`**: Corresponde a todos os valores possíveis para o campo.
- **`,`**: Lista de valores. Exemplo: `1,2,5` (executa no minuto 1, 2 e 5).
- **`-`**: Intervalo de valores. Exemplo: `1-5` (executa nos minutos 1, 2, 3, 4, 5).
- **`/n`**: Incremento. Exemplo: `*/10` (executa a cada 10 minutos).

### 2. **Tarefas Agendadas Únicas com `at`**

Enquanto o `cron` é usado para tarefas repetitivas, o comando **`at`** é utilizado para agendar tarefas que precisam ser executadas uma única vez em um momento específico no futuro.

#### Comandos Básicos do `at`:

- **Agendar uma tarefa com `at`**:
  ```
  at [hora] [data]
  ```
  Esse comando entra no modo de inserção de comandos para o `at`. Após inserir os comandos desejados, pressione `Ctrl + D` para salvar e sair.

- **Verificar tarefas agendadas com `atq`**:
  ```
  atq
  ```
  Exibe a lista de tarefas agendadas com `at`.

- **Cancelar uma tarefa agendada com `atrm`**:
  ```
  atrm [job_id]
  ```
  Cancela uma tarefa agendada. O `job_id` é o identificador da tarefa, obtido com o comando `atq`.

#### Exemplo de Agendamento com `at`:

1. **Agendar a execução de um script às 14h de hoje**:
   ```
   at 14:00
   ```
   Após pressionar `Enter`, o sistema entrará no modo de inserção de comando. Digite o comando a ser executado, por exemplo:
   ```
   /home/usuario/scripts/backup.sh
   ```
   Depois pressione `Ctrl + D` para sair e salvar a tarefa.

2. **Agendar uma tarefa para ser executada amanhã às 10h**:
   ```
   at 10:00 tomorrow
   ```
   Digite o comando desejado e finalize com `Ctrl + D`.

### 3. **Gerenciamento de Tarefas Agendadas**

- **Monitorando Tarefas do `cron`**:
  - As saídas dos comandos executados pelo cron são normalmente enviadas por e-mail ao usuário, mas você pode redirecionar a saída para um arquivo ou para `/dev/null` (se não quiser receber notificações).
  - Exemplo de redirecionamento para `/dev/null`:
    ```
    0 2 * * * /home/usuario/scripts/backup.sh > /dev/null 2>&1
    ```
    Nesse exemplo, a saída padrão e os erros (`2>&1`) são redirecionados para `/dev/null`.

- **Visualizando Logs do `cron`**:
  - Os logs de execução das tarefas agendadas pelo `cron` geralmente são armazenados em `/var/log/syslog` ou `/var/log/cron`. Você pode visualizar esses logs para verificar se as tarefas foram executadas corretamente.

#### Exemplo de Comando para Visualizar Logs:
```
grep CRON /var/log/syslog
```

### Conclusão

Agendar tarefas no Linux, seja de forma recorrente com o `cron` ou única com o `at`, é uma prática fundamental para a automação de processos e manutenção do sistema. Essas ferramentas permitem que tarefas como backups, limpeza de arquivos, atualizações e outras operações sejam realizadas automaticamente, sem a necessidade de intervenção manual, garantindo a eficiência e a segurança do ambiente.

