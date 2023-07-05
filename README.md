# Projeto - Instalação da aplicação Web Allsafe Express

O objetivo desse projeto é subir uma aplicação em um servidor apache2 que precisa se autenticar a um banco de dados mariadb.

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

  
