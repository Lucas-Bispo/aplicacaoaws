Criar um projeto de compilação com o GitHub como o repositório de origem e habilitar webhooks (console)
Abrir oAWS CodeBuildConsole dohttps://console.aws.amazon.com/codesuite/codebuild/home.

Em caso de CodeBuild A página de informações do é exibida, selecioneCriar um projeto de compilação. Caso contrário, no painel de navegação, expandaBuild, escolhaProjetos de compilaçãoe, depois, escolhaCriar um projeto de compilação.

Selecione Create build project (Criar projeto de compilação).

Em Configuração de projetos:

Nome do projeto
Insira um nome para esse projeto de compilação. Os nomes de projeto de build devem ser únicos em cada conta AWS. Você também pode incluir uma descrição opcional do projeto de compilação para ajudar outros usuários a entender para que esse projeto é usado.

Em Source (Origem):

Provedor de origem
SelecioneGitHub. Siga as instruções para se conectar (ou se reconectar) ao GitHub Escolha e, depois, escolhaAutorizar.

Repositório
Escolha Repositório em minha conta GitHub.

Repositório GitHub
Insira o URL do GitHub repositório do.

DentroEventos de webhook de origem primária, selecione o procedimento a seguir.

nota
OEventos de webhook de origem primáriaseção só estará visível se você escolherRepositório no meu GitHub contaNa etapa anterior.

Selecione Rebuild every time a code change is pushed to this repository (Recompilar toda vez que uma alteração de código for enviada para este repositório) ao criar seu projeto.

Em Event type (Tipo de evento), escolha um ou mais eventos.

Para filtrar quando um evento aciona uma compilação, em Start a build under these conditions (Iniciar uma compilação sob estas condições), adicione um ou mais filtros opcionais.

Para filtrar quando um evento não é acionado, em Don't start a build under these conditions (Não iniciar uma compilação sob estas condições), adicione um ou mais filtros opcionais.

SelecioneAdicionar grupo de filtrosPara adicionar outro grupo de filtros, se necessário.

Para obter mais informações sobre GitHub tipos e filtros de eventos webhook, consulteEventos de webhook do GitHub.

Em Environment (Ambiente):

Imagem do ambiente
Escolha uma das seguintes opções:

Para usar uma imagem do Docker gerenciada porAWS CodeBuild:
SelecioneImagem gerenciadae, em seguida, faça seleções deSistema operacional,Tempo (s) de execução,Imagem, eVersão da imagem. Faça uma seleção em Environment type (Tipo de ambiente) se estiver disponível.

Para usar outra imagem do Docker:
SelecioneImagem personalizada. para oTipo de ambiente, escolhaBRAÇO,Linux,GPU do Linux, ouJanela. Se você selecionar Other registry (Outro registro), em External registry URL (URL de registro externo), insira o nome e a tag da imagem do Docker no Docker Hub usando o formato docker repository/docker image name. Se escolherAmazon ECR, Uso doRepositório do Amazon ECReImagem do Amazon ECRpara escolher a imagem do Docker em seuAWSconta.

Para usar uma imagem privada do Docker:
SelecioneImagem personalizada. para oTipo de ambiente, escolhaBRAÇO,Linux,GPU do Linux, ouJanela. Em Image registry (Registro da imagem), selecione Other registry (Outro registro) e insira o ARN das credenciais da imagem privada do Docker. As credenciais devem ser criadas pelo Secrets Manager. Para obter mais informações, consulte O que é o AWS Secrets Manager? no Guia do usuário do AWS Secrets Manager.

Função de serviço
Escolha uma das seguintes opções:

Se você não tiver uma CodeBuild função de serviço, escolhaNova função de serviço. No campo Role name, digite o nome da nova função.

Se você tiver um CodeBuild função de serviço, escolhaFunção de serviço existente. DentroARN de função, escolha a função de serviço.

nota
Quando usar o console para criar ou atualizar um projeto de build, você pode criar um CodeBuild Função de serviço ao mesmo tempo. Por padrão, a função funciona somente com esse projeto de build. Se você usar o console para associar essa função de serviço a outro projeto de compilação, a função será atualizada para funcionar com os outros projetos de compilação. Uma função de serviço pode funcionar com até 10 projetos de compilação.

DentroBuildspec, siga um destes procedimentos:

SelecioneUsar um arquivo buildspecPara usar o arquivo buildspec.yml no diretório raiz do código-fonte.

SelecioneInserir comandos de construçãopara usar o console para inserir comandos de compilação.

Para mais informações, consulte Referência de buildspec.

Em Artefatos:

Type
Escolha uma das seguintes opções:

Se você não quiser criar artefatos de saída de compilação, selecione No artifacts (Nenhum artefato).

Para armazenar a saída de compilação em um bucket do S3, escolhaAmazon S3e faça o seguinte:

Se você quiser usar o nome do projeto para a pasta ou arquivo ZIP de saída da compilação, deixe Name (Nome) em branco. Caso contrário, insira o nome. Por padrão, o nome do artefato é o nome do projeto. Se você quiser usar um nome diferente, insira-o na caixa de nome do artefato. Se você quiser gerar um arquivo ZIP, inclua a extensão zip.

Para Bucket name, selecione o nome do bucket de saída.

Se você tiver escolhido Insert build commands (Inserir comandos de compilação) anteriormente neste procedimento, em Output files (Arquivos de saída), insira os locais dos arquivos da compilação que deseja incluir na pasta ou no arquivo ZIP de saída da compilação. Para vários locais, separe-os com uma vírgula (por exemplo, appspec.yml, target/my-app.jar). Para obter mais informações, consulte a descrição de files em Sintaxe de buildspec.

Configuração adicional
Expanda Additional configuration (Configuração adicional) e defina as opções conforme apropriado.

Selecione Create build project (Criar projeto de compilação). Na página Review (Revisão), escolha Start build (Iniciar compilação) para executar a compilação.

Verificações
Abrir oAWS CodeBuildConsole dohttps://console.aws.amazon.com/codesuite/codebuild/home.

No painel de navegação, selecione Build projects.

Execute um destes procedimentos:

Selecione o link do projeto de compilação com webhooks que você deseja verificar e selecione Detalhes da compilação.

Selecione o botão ao lado do projeto de compilação com webhooks que você deseja verificar, escolhaView details (Visualizar os detalhes)e, depois, escolha oDetalhes da compilaçãoguia.

DentroEventos de webhook de origem primária, escolha oWebhookLink de URL.

No seu GitHub repositório, noConfiguraçõespágina, emWebhooks, verifique seSolicitações pulleEmpurrasão selecionados.

No seu GitHub configurações de perfil, emConfigurações pessoais,Aplicativos,Aplicativos OAuth autorizados, você deve ver que seu aplicativo foi autorizado a acessar oAWSRegião que você selecionou.
