# Módulo 5: Redes e Segurança


### Módulo 5: Redes e Segurança

Neste módulo, exploraremos os conceitos fundamentais de rede no Linux e a importância da segurança do sistema. O gerenciamento de redes e a proteção contra ameaças são essenciais para manter o sistema estável e seguro. O Linux, sendo amplamente utilizado em servidores e infraestrutura de rede, oferece um conjunto robusto de ferramentas para administrar redes e garantir a segurança de arquivos, serviços e dados.

---

#### 1. **Conceitos Básicos de Rede**

O Linux possui um conjunto de ferramentas poderosas para o gerenciamento de redes, permitindo aos usuários configurar, monitorar e diagnosticar conexões de rede. Aqui estão alguns conceitos e comandos fundamentais relacionados à rede em sistemas Linux.

##### 1.1. **Endereço IP e Máscara de Rede**
- O **endereço IP** identifica de forma única um dispositivo em uma rede. Ele pode ser **IPv4** (um endereço de 32 bits, como `192.168.0.1`) ou **IPv6** (um endereço de 128 bits, como `2001:0db8:85a3::8a2e:0370:7334`).
- A **máscara de rede** define quais partes de um endereço IP pertencem à rede e quais partes identificam o host. Por exemplo, a máscara `255.255.255.0` ou `/24` indica que os três primeiros octetos representam a rede e o último identifica o host.

##### 1.2. **Interfaces de Rede**
Uma interface de rede é o ponto de conexão entre o sistema e a rede. No Linux, as interfaces de rede podem ser físicas (como placas de rede Ethernet) ou virtuais (como interfaces criadas por VPNs).

- As interfaces de rede são nomeadas de forma padrão, como **`eth0`** para Ethernet e **`wlan0`** para Wi-Fi, embora nas versões mais recentes do Linux elas sigam um esquema de nomeação previsível (por exemplo, **`enp0s3`**).

##### 1.3. **Comandos Básicos de Rede**
- **`ip`**: O comando principal para gerenciar interfaces de rede, endereços IP, roteamento, etc.
  - Exibir informações sobre as interfaces de rede:
    ```
    ip a
    ```
  - Atribuir um endereço IP a uma interface:
    ```
    sudo ip addr add 192.168.0.10/24 dev eth0
    ```
  - Ativar ou desativar uma interface de rede:
    ```
    sudo ip link set eth0 up
    sudo ip link set eth0 down
    ```

- **`ifconfig`**: Um comando mais antigo (ainda amplamente utilizado) para configurar interfaces de rede e visualizar detalhes da conexão.
  - Exibir informações sobre as interfaces de rede:
    ```
    ifconfig
    ```

- **`ping`**: Verifica a conectividade entre o seu sistema e outro dispositivo na rede enviando pacotes ICMP.
  - Para testar a conexão com um servidor remoto (por exemplo, o Google DNS):
    ```
    ping 8.8.8.8
    ```

- **`netstat`**: Exibe informações detalhadas sobre conexões de rede ativas, tabelas de roteamento e estatísticas de rede.
  - Ver todas as conexões de rede ativas:
    ```
    netstat -tuln
    ```

- **`traceroute`**: Exibe o caminho que um pacote percorre para alcançar o destino.
  - Para ver o caminho até um servidor remoto:
    ```
    traceroute google.com
    ```

- **`nslookup` e `dig`**: Ferramentas para consultar servidores DNS e verificar a resolução de nomes de domínio.
  - Para consultar o endereço IP associado a um domínio:
    ```
    nslookup google.com
    ```

##### 1.4. **Roteamento e Tabela de Roteamento**
O **roteamento** no Linux define como os pacotes de rede são enviados de um sistema para outro através de uma rede. A tabela de roteamento armazena informações sobre os caminhos disponíveis para diferentes redes.

- Para visualizar a tabela de roteamento:
  ```
  ip route show
  ```
  ou
  ```
  netstat -r
  ```

---

#### 2. **Introdução à Segurança no Linux**

A segurança é um componente crítico em qualquer sistema operacional, e o Linux oferece diversas ferramentas e práticas para garantir a proteção de dados e a integridade do sistema. A seguir, veremos os conceitos e ferramentas fundamentais para aumentar a segurança no Linux.

##### 2.1. **Gerenciamento de Permissões**
O Linux utiliza um sistema de permissões para controlar o acesso a arquivos e diretórios, o que é crucial para a segurança. Cada arquivo tem permissões para **usuário** (dono), **grupo** e **outros**, e pode conceder permissões de leitura (r), escrita (w) e execução (x).

- Para verificar as permissões de um arquivo:
  ```
  ls -l arquivo.txt
  ```
  Exemplo de saída:
  ```
  -rw-r--r-- 1 usuario grupo 1024 Jan 1 12:00 arquivo.txt
  ```
  Isso significa que o **usuário** pode ler e escrever o arquivo, enquanto o **grupo** e **outros** podem apenas lê-lo.

- Para alterar as permissões de um arquivo:
  ```
  chmod u+x arquivo.sh   # Concede permissão de execução ao usuário
  chmod g-w arquivo.txt  # Remove permissão de escrita do grupo
  ```

##### 2.2. **Usuário Root e o Comando `sudo`**
No Linux, o usuário **root** é o administrador com controle total do sistema. Para evitar o uso constante da conta root, o comando `sudo` é utilizado para conceder permissões administrativas a usuários comuns temporariamente.

- Usar `sudo` para executar comandos como root:
  ```
  sudo apt update
  ```

- Adicionar um usuário ao grupo `sudo` para conceder privilégios administrativos:
  ```
  sudo usermod -aG sudo nome_do_usuario
  ```

##### 2.3. **Firewall com `ufw`**
O **UFW** (Uncomplicated Firewall) é uma ferramenta simples para gerenciar o firewall no Linux. Ele é uma interface amigável para o **iptables**, tornando a configuração do firewall mais acessível para usuários menos experientes.

- Ativar o firewall:
  ```
  sudo ufw enable
  ```

- Permitir conexões SSH:
  ```
  sudo ufw allow ssh
  ```

- Bloquear uma porta específica:
  ```
  sudo ufw deny 8080
  ```

- Verificar o status do firewall:
  ```
  sudo ufw status
  ```

##### 2.4. **Atualizações de Segurança**
Manter o sistema atualizado é uma das maneiras mais eficazes de garantir a segurança. O Linux tem atualizações frequentes para corrigir vulnerabilidades e bugs.

- Para atualizar todos os pacotes e aplicar correções de segurança:
  ```
  sudo apt update && sudo apt upgrade
  ```

##### 2.5. **Logs de Segurança**
Os logs do sistema são uma ferramenta essencial para monitorar e detectar atividades suspeitas. No Linux, os logs são armazenados em `/var/log/`. Alguns dos logs importantes são:
- `/var/log/auth.log`: Registra as tentativas de autenticação.
- `/var/log/syslog`: Contém informações sobre o sistema e seus serviços.

Para visualizar logs em tempo real:
```
tail -f /var/log/auth.log
```

#### Conclusão

O gerenciamento de redes e a segurança são componentes fundamentais no Linux. Com o conhecimento básico sobre a configuração de rede e as ferramentas disponíveis para aumentar a segurança, os usuários podem garantir que seus sistemas estejam conectados e protegidos de ameaças. O Linux oferece uma ampla gama de ferramentas de segurança que, quando usadas corretamente, tornam o sistema extremamente robusto e confiável.
