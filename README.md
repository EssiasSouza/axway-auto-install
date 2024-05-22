ATENÇÃO: NÃO EXCLUA ARQUIVOS OU ESTE DIRETÓRIO.

Esse diretório foi criado para corrigir possíveis problemas com o Axway, por este motivo vamos mantê-lo.

===================================================
Autor: Essias Souza <essias.souza@fleetcor.com.br>
Dezembro de 2023.

Este documento visa auxiliar no uso do script de instalação automática de forma não assistida.

COMO FUNCIONA?

 - O Script executa a instalação do Axway usando o except que interage automaticamente com o script não sendo necessária a interação do usuário.
 - Para um bom funcionamento deve-se notar os seguintes pontos.

1 - Na pasta /home/pi/instalador_Axway deve conter os seguintes arquivos.
  - Activator_6.1_Install_linux-x86-64_BN6.sh
  - autoInstall_EDI_Axway.sh
  - Axway_autoInstall.sh
  - License.xml
  - README.txt

2 - O arquivo Axway_autoInstall.sh precisa estar com permissão 777

EXECUÇÃO

- No terminal rode os seguintes comandos

sudo ls -l # Com essa linha você ira elevar para super usuário seu login

# Este comando a seguir irá rodar em segundo plano e você poderá fechar o terminal que o comando estará rodando em segundo plano.
sudo nohup /home/pi/instalador_Axway/autoInstall_EDI_Axway.sh > /home/pi/instalador_Axway/AutoInstall_EDI_Axway$(date +%Y%m).log 2>&1 & disown

VALIDAÇÕES

- Ao terminar a execução do comando haverá um arquivo de log dentro da pasta /home/pi/instalador_Axway/ onde você poderá validar a instalação se ocorreu algum erro.
- Valide se o arquivo autoStartAbastece.sh está com o edi e ediSupport sem comentários.
- Abra o navegador e acesse a console de configuração para validar o serviço. Você também pode validar se o serviço subiu analisando o log com o segguinte comando.

tail -f /home/pi/Axway/Activator/logs/server.log