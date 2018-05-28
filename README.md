# Ambiente Laravel (config inicial) (testado em Ubuntu 16.04 LTS e 18.04 LTS)
# Link instalação NetInstall do Ubuntu
http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-amd64/current/images/netboot/mini.iso

O script será responsável  pela instalação do Mysql, PHP, PHPMyAdmin, Openssh, Composer, Redis.

Funcionamento é simples, só clonar o repositório e executar setup.sh 
(caso nescessario de permissão de execução ao arquivo, ``` chmod +x setup.sh ```)

Abaixo tambem há alguns passos para caso precise acessar o banco de dados remotamente.
(para mais detalhes consulte a documentação oficial)

##########################################################
#   Configuração para liberar o acesso remoto no mysql   #
##########################################################
# Acesse o arquivo mysqld.cnf
``` sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf```
# Comente a linha colocando o # na frente
``` #bind-address = 127.0.0.1 ```
# Acesse o mysql
``` mysql -u root -p ```
# Insira o comando a baixo substituindo a senha pela do mysql
``` GRANT ALL ON *.* TO 'root'@'%' IDENTIFIED BY 'senha' WITH GRANT OPTION; ```
# Execute os privilégios 
``` FLUSH PRIVILEGES; ```
# Saia do mysql
``` exit ```
# Reinicie o Mysql
``` sudo systemctl restart mysql ```
