Como usar?
===========

Faça o clone do repositório:::

    git clone https://github.com/agnogueira/clean.buildout.git

É importante trabalhar com **env** do python, assim você elimina a possibilidade
de estragar o ambiente. Para maiores informações leia a documentação em:
https://pypi.python.org/pypi/virtualenv

Após clonar, garanta que você esteja utilizando um virtualenv, e acesse a pasta
**cd clean.buildout** e execute os comandos para a montagem do ambiente.::

    penv2.7 bootstrap.py
    bin/buildout -N -t 30

Ao final você terá o ambiente devidamente contruído, então basta subir a
intância com o comando:::

    bin/instance start

Troque o **start** por **fg** caso queira subir em modo para debugar, para poder
parar a instância basta executar o mesmo comando trocando **start** por
**stop**.


Tenho um novo pacote como faço?
=================================

* Caso você tenha um novo produto, mas não está ainda no controle de versão (git,
svn e etc.), você deverá mover o seu produto para dentro da pasta **src**,
depois editar o arquivo **buildout.cfg** e especificá-lo na sessão **develop** e
também na lista de **eggs**.

* Caso seu produto esteja em uma repositório então deverá editar o
**basico.cfg** e na sessão **remotes** e **sources** adicioná-lo conforme o
modelo. Também deve listar o pacote na lista de **eggs**.

* Agora se você apenas deseja apenas adicionar um novo produdo e que não esteja
em desenvolvimento, basta editar o **buildout.cfg** e adicionar na lista de
**eggs**.

Após qualquer um dos passos acima, você deverá executar o buildout novamente:::

    bin/buildout -N -t 30

E então parar e subir sua instância com os comandos:::

    bin/instance stop
    bin/instance start
