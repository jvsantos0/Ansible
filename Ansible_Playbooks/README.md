# Explicação do Playbook

* Vale lembrar que utilizei o sistema operacional do Ubuntu Server para realizar os passos abaixo.

1. Inventário Utilizado:

	[localhost]\
	127.0.0.1
  
	[webservers]\
	vm1\
	vm2
  
	[dbservers]\
	vm3
  
	[logservers]\
	vm5

	[lamp:children]\
	webservers\
	dbservers

2. Criando registro DNS para as máquinas utilizadas ("vmX")\
	*sudo nano /etc/hosts*
  
	Já dentro do arquivo, bastas seguir a lógica do localhost que já vai estar escrito no mesmo.
  
	127.0.0.1 localhost\
	x.x.x.x vm1\
	x.x.x.x vm2\
	x.x.x.x vm3\
	x.x.x.x vm5

3. Testando as máquinas com o comando *ansible all -m ping*
	Antes de tentar o comando é importante que a máquina Ansible já tenha acesso SSH com as outras vms.
	
	Ativando o ssh-agent = eval `ssh-agent`
	
	Adicionando a chave as listas do ssh-agent = ssh-add *caminho do arquivo .pem*
	
	Comando para acesso ssh após o ssh-agent cadastrar a chave = ssh ubuntu@vmX *onde está o X basta modificar pelo número da VM de 1-5
	Após a máquina Ansible ter acesso a todas as outras 4 VM's, o comando citado no tópico pode dar erros referente ao python das máquinas alvo. Basta entrar nas máquinas e dar um apt-get update e verificar se o python foi instalado. Caso não tenha sido, basta baixar o pacote do python com o apt-get install python3
	
4. Prosseguindo para o Playbook

