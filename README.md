## AXWAY AUTO INSTALL
Maio de 2024.

## OBJETIVO DO PROJETO.
O Script executa a instalação do Axway usando o except que interage automaticamente com o script não sendo necessária a interação do usuário. Dessa forma o script faz a instalação de forma não assistida. São dois scripts com as seguintes finalidades:
 - **autoInstall_Activator6.1.sh** que faz a instalação do Axway Activador 6.1 apenas de forma automática, dando enters e digitando os caminhos de pastas, licença e etc.
 - **reinstall_Axway.sh** que faz um comentário no arquivo usado pelo crontab evitando que o serviço tente reiniciar, para o serviço do Axway Activator se estiver rodando, deleta os arquivos da pasta do Axway, faz a instalação e remove os comentários no arquivo de auto start.

### DEPENDENCIAS

A aplicação depende do arquivo de instalação do Axway Activator e da licença além de rodar apenas em sistemas Linux.

### COMO RODAR?

Para um bom funcionamento deve-se notar os seguintes pontos.

1 - Na pasta /home/pi/ deve conter os seguintes arquivos:
  - Activator_6.1_Install_linux-x86-64_BN6.sh
  - License.xml

2 - O arquivo Axway_autoInstall.sh precisa estar com permissão executável

### EXECUÇÃO

No terminal rode os seguintes comandos

sudo ls -l # Com essa linha você ira elevar para super usuário seu login

**Este comando a seguir irá rodar em segundo plano e você poderá fechar o terminal que o comando estará rodando em segundo plano.**

sudo nohup /suporte/axwayautorecovery/robot/autoInstall_Activator6.1.sh > /suporte/axwayautorecovery/logs/autoInstall_Activator6.1$(date +%Y%m).log 2>&1 & disown

Ou para reinstalar:

sudo nohup /suporte/axwayautorecovery/robot/reinstall_Axway.sh > /suporte/axwayautorecovery/logs/reinstall_Axway$(date +%Y%m).log 2>&1 & disown

VALIDAÇÕES

- Ao terminar a execução do comando haverá um arquivo de log dentro da pasta /suporte/axwayautorecovery/logs onde você poderá validar a instalação se ocorreu algum erro.
- Valide se o arquivo autoStartAbastece.sh está com o edi e ediSupport sem comentários.
- Abra o navegador e acesse a console de configuração para validar o serviço. Você também pode validar se o serviço subiu analisando o log com o segguinte comando.

tail -f /home/pi/Axway/Activator/logs/server.log

ou

ediLog