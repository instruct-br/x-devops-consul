# **README**

Este projeto contém uma aplicação web com dois nós configurados em uma máquina virtual usando o Consul como ferramenta de gerenciamento de serviços. Um nó contém a aplicação backend em Flask e o outro contém a aplicação frontend em Vue que consome a API Flask.

## **Consul**

O Consul é uma ferramenta de gerenciamento de serviços que fornece recursos como descoberta de serviços, monitoramento de serviços, DNS interno e balanço de carga. Ele ajuda a garantir que os serviços estejam em execução e sejam acessíveis, mesmo em um ambiente distribuído.

O Consul usa um modelo de cliente/servidor, no qual os nós do Consul agem como clientes e servidores ao mesmo tempo. Isso significa que cada nó do Consul tem a capacidade de fornecer e consumir serviços.

## **Pré-requisitos**

- **[Vagrant](https://www.vagrantup.com/)** instalado
- **[VirtualBox](https://www.virtualbox.org/)** instalado

## **Instalação**

1. Clone este repositório em sua máquina local:

```
bashCopy code
git clone https://github.com/seu-usuario/nome-do-repositorio.git

```

1. Navegue até o diretório clonado:

```
javascriptCopy code
cd nome-do-repositorio

```

1. Inicialize a máquina virtual:

```
Copy code
vagrant up

```

1. Acesse a máquina virtual:

```
Copy code
vagrant ssh

```

1. Inicie o agente do Consul em cada nó:

```
Copy code
consul agent -dev

```

1. Inicie a aplicação backend em Flask em um nó:

```
bashCopy code
cd /vagrant/backend
export FLASK_APP=app.py
flask run --host=0.0.0.0 --port=5000

```

1. Inicie a aplicação frontend em Vue em outro nó:

```
bashCopy code
cd /vagrant/frontend
npm install
npm run serve -- --port=8080 --host=0.0.0.0

```

1. Abra o navegador e acesse a aplicação em **[http://localhost:8080](http://localhost:8080/)**.
