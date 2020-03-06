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
	x.x.x.x vm5\
