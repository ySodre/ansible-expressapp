# Projeto - Instalação da aplicação Web Allsafe Express

O objetivo desse projeto é fazer o deploy de uma aplicação web que faz consultas ao servido de banco de dados de maneira automatizada com o ansible.

## Conhecimentos utilizados
  <ul>
    <li>Ansible</li>
    <li>Estrutura de arquivos Ansible</li>
    <li>Código reutilizável</li>
    <li>Apache2</li>
    <li>Banco de dados</li>
    <li>Par de chaves pública e privada</li>
  </ul>

## Configuração

1 - Utilizei o vagrant para provisionar as instâncias do projeto: controle (ansible), web e db.

2 - Configuração da máquina controle

  <ul>
    <li>#apt update -y</li>
    <li>#apt install git -y</li>
    <li>#apt install ansible -y </li>
    <li>#cd /opt</li>
    <li>#mkdir expressapp</li>
    <li>#cd expressapp</li>
    <li>#git clone <strong>https://github.com/ySodre/ansible-expressapp.git</strong></li>
    <li>#cd ansible-expressapp</li>
 </ul>

3 - Gerar par de chaves para os servidor WEB e DB e importar para os servidores, por padrão o usuário e senha das máquinas provisionadas pelo vagrant é: vagrant.

  <ul>
    <li>#ssh-keygen</li>
    <li>#ssh-copy-id vagrant@ip_db</li>
    <li>#ssh-copy-id vagrant@ip_web</li>
  </ul>
4 - Editar o arquivo hosts dentro do diretorio do ansible_expressapp, alterando o IP dos servidores e o caminho da sua chave privada gerada.

## Testar comunicação com os servidores

  <ul>
    <li>#<strong>ansible -i hosts all -m ping</li>
  </ul>
      
  Você deverá ver o seguinte retorno.
      
  ![image](https://github.com/ySodre/ansible-expressapp/assets/89286829/ac0f7557-a632-4f28-bb58-0cb430fb397c)

## Executar o playbook implementação

Nesse projeto existe apenas uma váriável de ambiente que é o IP do banco de dados então no momento da execução é necessário passar a váriavel informando qual o IP do servidor de banco de dados.

  <ul>
    <li>#ansible-playbook -i hosts -e "db_ip=ip_db" playbook.yaml </li>
  </ul>

Ao finalizar você deverá ver o resultado das tarefas sem erros

![image](https://github.com/ySodre/ansible-expressapp/assets/89286829/b0d45ff6-cd68-48fd-86a3-6e4eb3ac8ada)

## Configuração DNS

Como estamos trabalhando com IPs privados, será necessário editar o arquivo hosts da sua máquina e criar o apontamento necessário.

Exemplo em windows. Caminho: C:\Windows\System32\drivers\etc\hosts

![image](https://github.com/ySodre/ansible-expressapp/assets/89286829/925eb3f2-a15a-4452-8abc-4d9f9f0ad964)

Exemplo em Linux. Caminho /etc/hosts

![image](https://github.com/ySodre/ansible-expressapp/assets/89286829/d1124001-5bb0-4491-9f72-a42c7c9db640)

## Resultado

O resultado esperado é que ao digitar express.asf.com abra o website da aplicação e além disso na guia de backups precisa aparecer dois backups, validando a comunicação com o banco de dados.

![image](https://github.com/ySodre/ansible-expressapp/assets/89286829/2a4ef44b-240f-4862-8c9c-9cc35e454de3)

![image](https://github.com/ySodre/ansible-expressapp/assets/89286829/2dc13b09-1509-4099-b3d8-e09b18dd02a9)





