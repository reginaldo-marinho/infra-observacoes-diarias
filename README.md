# Rapidinhas 

<div style="padding: 20px; background-color: #ffc107; border-radius: 5px; box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);">
  <p><strong>Cuidado!</strong> Esse Documento é Apenas um Rascunho.</p>
</div>


## Introdução

Desenvolver aplicativos profissionais em quaisquer que sejam as tecnologias, requerem certamente pelo menos dois ambientes, `development` e `production`. Enquanto um tem foco principal nos detalhes do desenvolvimento, trazendo informações mais detalhas sobre a pilha de recursos que fazem parte do sistema como um todo o outro tem foco principal em fornecer o melhor da segurança, velocidade e simplicidade nos seus eventos internos.    

## Variáveis de Ambiente

- Os ambientes no aspnet podem ser alternados atravéz das variáveis de ambiente `ASPNETCORE_ENVIRONMENT` ou `DOTNET_ENVIRONMENT`
    - Existe precedencia entre `ASPNETCORE_ENVIRONMENT` e `DOTNET_ENVIRONMENT`. **É importante saber qual tem prioridade com base no projeto desenvolvido**
    - Para ambas `launchSettings.json` define o valor `development` como padrão
    - Produção (`production`) só é aplicado quando  `ASPNETCORE_ENVIRONMENT` ou `DOTNET_ENVIRONMENT` não é definidas
    - Definir variáveis
        - No processo
            ```shell
            # Cada tipo de console tem uma sintaxe diferente
            set ASPNETCORE_ENVIRONMENT=Staging
            dotnet run --no-launch-profile
            ```
        - Definir variáveis Globalmente
            - [Windows](https://www.oobj.com.br/bc/article/como-configurar-variavel-de-ambiente-no-windows-para-emiss%C3%A3o-de-mf-e-1180.html)
            - Linux
        - Definir variáveis Configs
            - [web.config](https://learn.microsoft.com/pt-br/aspnet/core/host-and-deploy/iis/web-config?view=aspnetcore-8.0#set-environment-variables)
            - [IIS](https://learn.microsoft.com/pt-br/aspnet/core/host-and-deploy/visual-studio-publish-profiles?view=aspnetcore-8.0)
    
## launchSettings

- `Properties/launchSettings.json`
    - **Define diferentes perfis**
        - Podemos escolher o perfil pela CLI `dotnet run --launch-profile "MeuPperfil"`

    - **Deve ser usado apenas no cumputador local**
    - **Não é implantado**.
    - **As variavies de ambiente definidas aqui substituem as definidas pelo sistema**
    - **Não guarde segredos|senhas nesse aquivo**

- `.vscode/launch.json`
    - É uma alternativa para  `Properties/launchSettings.json`? **Estudar**
- Para mudar o ambiente via linha de comando usamos
    - `dotnet run --environment Production`

## Perfis de Publicação
- `Properties/PublishProfiles` são opções usadas na publicação do projeto

## Strings de Conexão
- Criptografia
- Devem sempre vir de algum arquivo de configuração, e mesmo assim não deve ter dados confidenciais expostos
- Não deixar senhas e se possível o nome do banco de dados exposto

## Secrets Manager


## Sobre ambientes de Produção

- Deve Maximizar a segurança, o desempenho e a robustez do aplicativo
    - Frontend
        - Minificadores -  `min.css`, `min.js`
        - Empacotadores
        - Servidos via CDN

- Memoria
    - Cache
    - Páginas de erro
        - Diagnóstico desabilitadas.
        - Paginas Amigáveis habilitadas.
    - Log
        - Monitoramento de produção habilitados
        - Logs (Que fazem sentido)

## Publicar o APP

- CLI `dotnet publish`
    - Compila o Projeto e publica o resultado
    - Arquivos de saida
        - .dll
        - .deps.json
        - .runtimeconfig.json 
    - Sua saida pode ser  usada por sistemas de hospedagem
        - apache
        - iis
        - nginx
    - [Referencia](https://learn.microsoft.com/pt-br/dotnet/core/tools/dotnet-publish)
     
    
- inetpub
    - É a pasta padrão do Microsoft Internet Information Services (IIS)
    - Fornece informações de Logs 
    - Fornece sites em wwwroot
        - **Se o site informado estiver fora da pasta `ìnetpub`, possivelmente terá erros de permissções, fique atento!**
    - entre  outras coisas 


## Debug (F5)

O modo debug é o  modo padrão que ocorre quando inicializamos um aplicativo com F5, ao inicializar dessa forma, é anexado o depurador ao processo atual, assim, **é possível saber detalhadamente e com tempo humano o comportamento da aplicação**.

- Opções de Etapas 
    - F9 (Interrupção)
    - F11 (Intervir)
    - F10 (Ignora Entrada)

- Janela Ponto de Função
    - Auxilia em Interrupções mais sofisticadas
    
### Anexando Processos com Visual Studio

Além do debug comum, podemos também atrelar nossos processos a nossa IDE de modo que a depuração ocorra também em processos criados a partir de outras aplicações, como o IIS por exemplo.


## Observações Diárias
- Para um melhor controle de versão durante o desenvolvimento de novas funcionalides e/ou melhorias, é muito importante que antes do desenvolvimento propriamente dito, tenha algum documento que indique a real razão. Isso é importante para dar mais sentido sobre o contexto, de modo que ao realizado, seja possível saber o por quê, os impactos, as pessoas relacionadas e o que pode ou não mudar com isso. Dito isso, **é afirmativo que é impossivel controlar o ciclo de vida do software sem saber as razões que o fizeram estar no seu estado atual.**
    - Por isso
        - Ter por exemplo um contado com o cliente diretamente por zap pode ser bom, mas é importante que sempre haja um chamado/ e-mail(assunto) que seja único ao ponto de ser amarrado ao desenvolvimento própriamente dito.

- Ter um projeto de software que tenha uma boa estrutura, com um ótimo designer, de modo que ao analisar seja possível saber seu real objetivo, é um ponto muito importante para ter profissionais com menos experiências, mas que ao ter as ferramentas em mãos, sejam capazes de ter mais facilidade de resolver outros problemas. Por exemplo, uma classe CRUD genérica pode ser um tanto quanto facilitadora para quem não conhece por exemplo o Entity Framework, que se usada a partir de Injeção de Depêndencia  ou por herança, já eliminamos, oportunidades de embaraços de conhecimentos  que unicialmente não fazem sentido para o Nínel de conhecimento do desenvolvedor, mas que no contexto empregado, o problema é resolvido e o agente da solução poderá ter mais tempo para aprender sobre conceitos e por em prática por exemplo  em projetos pessoais.

- Ao desenvolvermos software não podemos desenvolver modelos que dominios pensando em uma estrutura de tabela, devemos garantir que nossas classes representem de fato o modelo de dominio. **A abordagem Code First do Entity Framework para novos desenvolvedores turva esse pensamento**.


## SQL Server
- CTE  [WITH](https://learn.microsoft.com/pt-br/sql/t-sql/queries/with-common-table-expression-transact-sql?view=sql-server-ver16) Com esse comando conseguimos ter mais legibilidade na criação de Consultas