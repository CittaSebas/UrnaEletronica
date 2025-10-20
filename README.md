# UrnaEletronica
Projeto da aula modelagem de Software. 

Integrantes:
 - Sebastian Citta 24.123.068-9
 - Juan Manuel Citta 24.123.022-6
 - João Pedro Bazoli Palma 24.123.041-6


<br>

## Diagrama de Atores
<img width="643" height="589" alt="image" src="https://github.com/user-attachments/assets/00a75dbb-4862-4d29-85b8-ece95b65baa3" />
<br>

## Casos de Uso

| Identificação | UC - 01 |
|---|---|
| Função | Cadastrar a Urna | 
| Atores | Gerente | 
| Prioridade | Essencial | 
| Pré-Condição | Urna em estado funcional | 
| Pós-Condição | Urna terá as informações cadastradas nela e está pronta para ser enviada ao local de votação | 
| Fluxo Principal | * O gerente entra no módulo UEg <br> * O gerente seleciona região <br> * O gerente entra com ID de uma Urna da região <br> * O gerente carrega a Lista de Candidatos da Região na Urna    |


<br>

| Identificação  | UC-02 |
|---|---|
| Função | Gerar relatório | 
| Atores | Gerente | 
| Prioridade | Essencial | 
| Pré-Condição | Votação concluída | 
| Pós-Condição | Será gerado um relatório com os resultados da votação, <br> apresentando os detalhes em formato de tabela ou gráficos | 
| Fluxo Principal | * O gerente acessa o sistema UEg <br> * O gerente entra no módulo "Gerar relatório" <br> * O gerente separa os resultados da votação por região <br> * O gerente separa os votos por cargo eleitoral <br> * O sistema totaliza os votos de cada categoria <br> * O gerente seleciona o modo de exibição do relatório <br> * O sistema gera o relatório  |

<br>

| Identificação | UC - 03 |
|---|---|
| Função | Validação da Urna | 
| Atores | Mesário, Urna | 
| Prioridade | Essencial | 
| Pré-Condição | A urna estar cadastrada | 
| Pós-Condição | Urna estará pronta para uso na votação e a emissão de um certificado da validade urna | 
| Fluxo Principal | * O mesário acessa o sistema UEv <br> * O mesário compara as informações da urna com as informações locais [FS01] <br> * O mesário registra a urna como funcional no UEg  <br> * O mesário emite um certificado confirmando que a urna está válida | 
| Fluxo Secundário [FS01] | * Os dados estão incongruentes com as informações do mesário <br> * O mesário registra a urna como não funcional em seu arquivo local e informa a gerência | 
<br>

| Identificação | UC - 04 |
|---|---|
| Função | Confirmar número de identificação | 
| Atores | Eleitor, Mesário , Urna| 
| Prioridade | Essencial | 
| Pré-Condição | Deve haver uma urna validada no local | 
| Pós-Condição | O eleitor pode prosseguir com o processo para votar | 
| Fluxo Principal | * O eleitor se apresenta com documento de identificação para o mesário <br> * O mesário acessa o Banco de Eleitores <br> * O mesário insere o número de identificação do documento no sistema <br> * O sistema valida o número [FS01] <br>   * O mesário informa ao eleitor qual urna deverá usar  | 
| Fluxo Secundário [FS01] | * O sistema não reconhece o número inserido <br> * O mesário pede ao eleitor para voltar com um número de identificação válido  |
<br>

| Identificação | UC - 05 |
|---|---|
| Função | Selecionar candidato | 
| Atores | Eleitor, Urna | 
| Prioridade | Essencial | 
| Pré-Condição | O eleitor deve possuir número de identificação validado e ter sido guiado a uma urna cadastrada e validada | 
| Pós-Condição | A urna conterá um candidato selecionado | 
| Fluxo Principal |  * A urna mostra a categoria a ser votada [FS01, FS02, FS03, FS04] <br> * O eleitor prossegue inserindo o número do candidato, a urna mostra a foto e o nome do candidato <br> * O eleitor confirma o voto selecionado apertando o botão "CONFRIMA" <br> * A urna registra o voto no candidato escolhido e registra separadamente que o eleitor já votou na UEv | 
| Fluxo Secundário [FS01] | * Eleitor aperta no botão "BRANCO" sem haver inserido nenhum número <br> * A urna informa que o voto será em branco e pede para o eleitor apertar o botão "CONFIRMA" <br> * A urna registra o voto em branco e registra separadamente que o eleitor já votou na UEv | 
| Fluxo Secundário [FS02] | * Eleitor insere um número não registrado a nenhum partido <br> * A urna informa que o voto será nulo e pede para o eleitor apertar o botão "CONFIRMA" <br> * A urna registra o voto nulo e registra separadamente que o eleitor já votou na UEv | 
| Fluxo Secundário [FS03] | * Eleitor insere apenas o número do partido e aperta "CONFIRMA" <br> * A urna informa que o voto será de legenda e pede para o eleitor apertar o botão "CONFIRMA" * A urna registra o voto de legenda e registra separadamente que o eleitor já votou na UEv | 
| Fluxo Secundário [FS04] | * Eleitor aperta no botão "CORRIGE" <br> * A urna apagará o número inserido | 

<br>

| Identificação | UC - 06 |
|---|---|
| Função | Encerrar votação | 
| Atores | Mesário, Urna | 
| Prioridade | Essencial | 
| Pré-Condição | Horário límite alcançado | 
| Pós-Condição | Urna não aceitará mais votos, e emitirá um relatório físico dos resultados e encaminhará a contagem dos votos à UEg | 
| Fluxo Principal | * O mesário acessa o sistema UEv  <br> * O mesário insere o código de encerramento na urna  <br> * O mesário seleciona o modo de exibição do relatório <br> * A urna imprime o relatório fisíco  <br> * A urna envia a contagem dos votos para a UEg  |  

<br><br>
## Diagrama de Classes
<br>
<img width="933" height="809" alt="image" src="https://github.com/user-attachments/assets/5336c14f-bc85-476d-9493-7dd8d51b91e3" />

<br><br>
## Diagramas de Sequência
<br>

### UC_01
```mermaid
sequenceDiagram
    actor Gerente
    participant UEg

    Gerente->>UEg: acessarModulo()
    Gerente->>UEg: selecionarRegiao()
    Gerente->>UEg: inserirIDUrna(id_urna)
    Gerente->>UEg: carregarListaCandidatos(regiao)
    UEg-->>Gerente: cadastrarUrna()
```
### UC_02

```mermaid
sequenceDiagram
    actor Gerente
    participant UEg

    Gerente->>UEg: acessarModulo()
    Gerente->>UEg: separarResultadosPorUEv()
    Gerente->>UEg: totalizarResultados()
    Gerente->>UEg: selecionarModoExibicao()
    Gerente->>UEg: preparaRelatorio()
    Gerente->>UEg: gerarRelatorio()
    UEg-->>Gerente: relatorioGerado()
```

### UC_03
```mermaid
sequenceDiagram
    actor Mesário
    participant Urna

    Mesário->>Urna: validarUrna()
    Urna-->>Mesário: exibirCandidatos()
    Mesário->>Urna: compararInformacoes()
    Mesário->>UEg: registrarUrnaFuncional()
    alt Dados Incongruenntes
        Mesário->>UEg: registrarUrnaNaoFuncional()
        Mesário->>UEg: informarIncongruencia()
    end

```

### UC_04
```mermaid
sequenceDiagram
    actor Mesário
    participant Eleitor
    participant Banco de eleitores

    Mesário->>Eleitor: solicitarNumeroTitulo()
    Eleitor-->>Mesário: fornecerNumeroTitulo(numero)

    Mesário->>Banco de eleitores: validarNumeroTitulo(numero)
    Banco de eleitores-->>Mesário: EnviarInfoEleitor
    Mesário->>Eleitor: liberarUrna()

    alt Numero de titulo inválido
       Mesário-->>Eleitor: solicitarDocValido()
    end
```
### UC_05
```mermaid
sequenceDiagram
    actor Eleitor
    participant Urna
    participant UEg

    Eleitor->>Urna: inserirNumeroPartido()
    Urna-->>Eleitor: exibirNomePartido()

    Eleitor->>Urna: inserirNumeroCandidato()
    Urna-->>Eleitor: exibirDadosCandidato()

    %% Fluxo principal: Voto em Candidato
    Eleitor->>Urna: confirmarVoto()
    Urna->>Urna: registrarVoto()
    Urna->>UEg: receberVotos()
    UEg-->>Urna: statusOK
    Urna-->>Eleitor: emiteSomConfirmacao()

    %% Fluxos alternativos
    alt Voto em Branco
        Eleitor->>Urna: pressionarBranco()
        Urna-->>Eleitor: solicitarConfirmacao()
        Eleitor->>Urna: confirmarVoto()
        Urna->>Urna: registrarVotoBranco()
        Urna->>UEg: receberVotos()
        UEg-->>Urna: statusOK
        Urna-->>Eleitor: emiteSomConfirmacao()
    else Voto Nulo
        Eleitor->>Urna: inserirNumeroInvalido()
        Urna-->>Eleitor: informaVotoNulo()
        Eleitor->>Urna: confirmarVoto()
        Urna->>Urna: registrarVotoNulo()
        Urna->>UEg: receberVotos()
        UEg-->>Urna: statusOK
        Urna-->>Eleitor: emiteSomConfirmacao()
    end

    opt Correção
        Eleitor->>Urna: pressionarCorrige()
        Urna->>Urna: limparDados()
        Urna-->>Eleitor: exibeTelaInicial()
    end
```
### UC_06
```mermaid
sequenceDiagram
    actor Mesário
    actor Urna
    actor UEg

    Mesário-->>Urna: encerrarVotacao()
    Urna-->>Mesário: selecionarModoExibicao()
    Mesário-->>Urna: escolherModoExibicao()
    Urna-->>Mesário: imprimirRelatório()

    Urna-->>UEg: enviarVotos()
    UEg-->>Urna: receberVotos()
```
## Diagrama de Estados
<br>
<img width="721" height="217" alt="image" src="https://github.com/user-attachments/assets/1158f6ff-4370-433e-8bc0-e4cdd26f9787" />
<br>

<img width="780" height="201" alt="image" src="https://github.com/user-attachments/assets/d8d2513e-cda2-4211-bcd2-97e036bc9013" />
<br>

<img width="542" height="219" alt="image" src="https://github.com/user-attachments/assets/cedad9b2-8397-40a5-b3da-b84bb9bd1348" />
<br>

## Diagrama de atividades
### Cadastro de urna
<img width="1363" height="373" alt="image" src="https://github.com/user-attachments/assets/dc24795e-e27d-4d6a-8a2d-3d024d81cbdb" />

### Encerrar a votação
<img width="682" height="577" alt="image" src="https://github.com/user-attachments/assets/bf3747e9-beba-4bce-a286-6341ff21872d" />


### Gerar relatório da votação
<img width="587" height="499" alt="image" src="https://github.com/user-attachments/assets/d5ec5cf1-d687-4eb5-938b-552b77ed55bf" />


### Validação da urna

<img width="643" height="513" alt="image" src="https://github.com/user-attachments/assets/2aa20c50-506d-4a7c-812f-93e3ac35e25f" />


### Confirmar número de identificação

<img width="905" height="548" alt="image" src="https://github.com/user-attachments/assets/b76b62ff-0bf9-4c96-b784-f544112ac97a" />


### Selecionar candidato

<img width="1048" height="595" alt="image" src="https://github.com/user-attachments/assets/33caae49-7fbd-4d98-9fd7-cf57e83ce2f9" />


## Diagrama de Componentes

<img width="1072" height="754" alt="image" src="https://github.com/user-attachments/assets/e90c7388-f96f-4150-95b0-da5ca0383044" />



