# Splunk InfoSec Installation Guide

## Instalação e configuração inicial do Splunk Enterprise
ETAPA 0: Configurando as VMs para o Laboratório 
Esta etapa é apenas se você precisar configurar uma VMs nova. 
O laboratório prático terá isso pronto antecipadamente.

### Firewall RHEL9
Verifique o status do firewalld:
Certifique-se de que o serviço firewalld está em execução.
```
sudo systemctl status firewalld
```

Adicione a exceção de porta TCP:
Use o comando firewall-cmd para adicionar a exceção de porta TCP.
Components and their relationship with the network - Splunk Documentation
```
sudo firewall-cmd --permanent --add-port=8000/tcp
```
```
sudo firewall-cmd --permanent --add-port=8089/tcp
```

Recarregue o Firewall:
Após adicionar a exceção de porta, recarregue o firewall para aplicar as alterações.
```
sudo firewall-cmd --reload
```
Verifique a Exceção:
Para verificar se a porta foi adicionada, liste todas as portas abertas.
```
sudo firewall-cmd --list-ports
```

 
Ulimit
Configure ulimit para o usuário que instalará o Splunk Enterprise (nesse caso splunkuser)
Link da documentação: 
https://www.splunk.com/en_us/blog/tips-and-tricks/whats-your-ulimit.html
https://docs.splunk.com/Documentation/Splunk/latest/Installation/Systemrequirements#Considerations_regarding_system-wide_resource_limits_on_.2Anix_systems
Edite a Configuração de Limites:
Abra o arquivo /etc/security/limits.conf em um editor de texto. (Dicas de Linux)
```
sudo vi /etc/security/limits.conf
```
Adicione as seguintes linhas para definir os valores de ulimit para o usuário splunk. Ajuste os valores conforme necessários com base no seu ambiente.
```
splunkuser soft nofile 64000
splunkuser hard nofile 64000
splunkuser soft nproc 16000
splunkuser hard nproc 16000
splunkuser soft fsize -1
splunkuser hard fsize -1
```
Salve as alterações e feche o arquivo.
Verifique as Configurações de Ulimit:
Mude para o usuário splunkuser e verifique as configurações de ulimit.
```
su - splunkuser
```
```
ulimit -n
ulimit -u
ulimit -f
```
Execute o comando abaixo para forçar as alterações
```
/sbin/sysctl -p
```
 
Transparent Huge Page
Desative Páginas de Memória Transparente (THP)
Verifique se o THP está habilitado
```
cat /sys/kernel/mm/transparent_hugepage/enabled
```
Se o comando acima retornar **[always]**, siga os passos abaixo para mudar para **[never]**
Abra o arquivo de configuração do GRUB em um editor de texto.
```
sudo vi /etc/default/grub
```
Adicione Parâmetros do Kernel:
Encontre a linha que começa com **GRUB_CMDLINE_LINUX** e adicione ```transparent_hugepage=never``` aos parâmetros do kernel.
No final, deve ficar assim: 
> GRUB_CMDLINE_LINUX="crashkernel=auto...transparent_hugepage=never"

Atualize o GRUB: Atualize a configuração do GRUB para aplicar as alterações.
```
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```
Adicione transparent_hugepage=never à linha de comando do kernel.
```
sudo grubby --args="transparent_hugepage=never" --update-kernel ALL
```
Reinicie o sistema para aplicar as alterações.
sudo reboot
Após reiniciar, verifique se o THP está desativado:
```
cat /sys/kernel/mm/transparent_hugepage/enabled
```
O resultado deve mostrar always madvise **[never]** indicando que o THP está desativado.

Dicas de Linux: 
Depois de entrar no modo de edição com o comando vi ou vim, pressione o botão Insert para começar a inserir as informações no arquivo.
Se pressionar Insert novamente entrará no modo Replace.
Pressione Esc para sair do modo Insert/Replace.
Para salvar e sair pressione :wq e depois Enter.
Para sair sem salvar pressione :q! e depois Enter. 

## Instalando o Splunk Enterprise

Crie um usuário para instalação e execução do Splunk Enterprise. 
```
sudo useradd -m -r splunkuser
```
```
sudo passwd splunkuser
```
Obs: Aparecerá uma mensagem de senha ruim, porém como é apenas um lab, seguiremos mesmo assim.
Credenciais: 
•	Usuário do SO: splunkuser
•	Senha do SO: splunkuser
Baixe Splunk TGZ
Link da versão mais recente: https://www.splunk.com/en_us/download/splunk-enterprise.html
```
wget -O splunk-9.4.0-6b4ebe426ca6-linux-amd64.tgz "https://download.splunk.com/products/splunk/releases/9.4.0/linux/splunk-9.4.0-6b4ebe426ca6-linux-amd64.tgz"
```
⚠️Para o lab de hoje o Splunk já está baixado no em /home/labuser/
```
cd /home/splunkuser/
```
Conceda permissão de execução no arquivo tgz e valide:
```
sudo chmod +x /home/labuser/splunk-9.4.0-6b4ebe426ca6-linux-amd64.tgz
```
```
sudo ls -lha /home/labuser
```
Crie o diretório de instalação (diretório padrão): 
```
sudo mkdir /opt/splunk
```
Mude as permissões do diretório para o usuário de execução: 
```
sudo chown -R splunkuser:splunkuser /opt/splunk
```
Verifique novamente as permissões da pasta.
```
ls -lha /opt/splunk
```
Instale o Splunk:
```
sudo tar -xzvf splunk-9.4.0-6b4ebe426ca6-linux-amd64.tgz -C /opt 
```

### Iniciando o Splunk
Inicie o Splunk aceitando os termos de licença e com o usuário correto.
sudo -H -u splunkuser /opt/splunk/bin/splunk start --accept-license 
Credenciais: 
•	Usuário do SO: splunkuser
•	Senha do SO: splunkuser
•	Nome de Usuário do Splunk: admin
•	Senha do Splunk: splunkuser
Habilite o Splunk para iniciar com o sistema e com o usuário de execução. 
Para garantir que o Splunk inicie utilizando o usuário correto, execute o seguinte comando após fazer login como splunkuser 
```
sudo /opt/splunk/bin/splunk enable boot-start -user splunkuser
```
```
sudo vi /etc/init.d/splunk
```
RETVAL=0 
USER=splunkuser
. /etc/init.d/functions

Comandos úteis

```
sudo -H -u splunkuser /opt/splunk/bin/splunk status
```
```
sudo -H -u splunkuser /opt/splunk/bin/splunk start
```
```
sudo -H -u splunkuser /opt/splunk/bin/splunk stop
```
```
sudo -H -u splunkuser /opt/splunk/bin/splunk restart
```
Links de referência:
https://docs.splunk.com/Documentation/Splunk/latest/Installation/RunSplunkasadifferentornon-rootuser
https://docs.splunk.com/Documentation/Splunk/latest/Admin/ConfigureSplunktostartatboottime#Enable_boot-start_as_a_non-root_user

## BOTSv3 Dataset

Instalar todos app listados aqui: https://github.com/splunk/botsv3
Podem instalá-los via GUI ou CLI.
```
cd /home/labuser/
```
```
sudo -H -u splunkuser /opt/splunk/bin/splunk stop
```
```
for file in *.tgz; do
       tar -xf "$file" -C /opt/splunktest/etc/apps/
   done
```
```
sudo tar -xvf botsv3_data_set.tgz -C /opt/splunk/etc/apps/
```
```
sudo chown -R splunkuser:splunkuser /opt/splunk
```
```
sudo -H -u splunkuser /opt/splunk/bin/splunk start
```
```
index=botsv3 earliest=0
```
