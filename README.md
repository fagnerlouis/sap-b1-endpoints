# B1 API Cookbook — Coleção Postman/Insomnia e Referência da API do SAP Business One Service Layer

> **Coleções Postman e Insomnia gratuitas e prontas para uso da API REST do SAP Business One (SAP B1) Service Layer.** Inclui 499 serviços e mais de 1.950 endpoints (Login, Business Partners, Items, Orders, Invoices, GL Accounts, e muito mais) com autenticação B1SESSION gerenciada automaticamente, esquemas de metadados OData V4 e guias de configuração amigáveis para iniciantes.

**Palavras-chave:** SAP B1 Postman Collection · SAP Business One Service Layer · SAP B1 REST API · SAP B1 Service Layer Postman · SAP B1 API Examples · SAP Business One OData V4 · B1s/v2 endpoints · SAP B1 Login Session · SAP B1 Integration · SAP B1 Developer Cookbook

## Visão Geral

O repositório `b1-api-cookbook` é um recurso completo para desenvolvedores que trabalham com as **APIs do SAP Business One (SAP B1) Service Layer**. Ele fornece informações detalhadas sobre os endpoints de serviço, esquemas de metadados e exemplos práticos para auxiliar tanto iniciantes quanto desenvolvedores experientes na integração com os serviços do SAP B1. Este repositório inclui:

- **Collections do Postman e Insomnia (prontas para importar)**: Coleções completas tanto para Postman (`postman/`) quanto para Insomnia (`insomnia/`) cobrindo todos os serviços expostos em `https://<your-server>:50000/b1s/v2/`, em par com arquivos de ambiente e gerenciamento automático de sessão/cookies.
- **Descrições de Serviço**: Arquivos JSON definindo os endpoints e operações para cada serviço.
- **Esquemas de Metadados**: Esquemas OData V4 (no formato EDMX) descrevendo os modelos de dados usados pelas APIs.
- **Guias para Iniciantes**: Instruções passo a passo para configurar e usar as APIs.
- **Exemplos de Código**: Exemplos práticos de chamadas de API para diversos serviços.

O objetivo deste repositório é simplificar a interação com o SAP B1 Service Layer, fornecendo documentação clara e exemplos reutilizáveis.

## Collections do Postman e Insomnia do SAP B1 Service Layer (Prontas para Uso)

Se você procurou por uma **Collection do SAP Business One no Postman**, **SAP B1 Service Layer no Insomnia**, ou uma **Collection da API REST do B1**, estes são os arquivos que você deseja.

### O que está incluído
- **499 pastas de serviços** cobrindo todo o SAP B1 Service Layer (`/b1s/v2/`).
- **Mais de 1.950 requisições pré-construídas** — `GET`, `POST`, `PATCH`, `DELETE` para entidades e chamadas de métodos de serviço.
- **Autenticação gerenciada automaticamente** — a requisição de `Login` captura o `SessionId` e o cookie `ROUTEID` para variáveis de ambiente; todas as outras requisições reutilizam eles automaticamente.
- **Arquivo de ambiente (Environment)** com `baseUrl`, `UserName`, `Password`, `CompanyDB`, `B1SESSION`, `ROUTEID`.
- **Formatos Nativos** — `postman_collection.json` para Postman e `insomnia_collection.json` (Workspace v4) otimizado especificamente para Insomnia.

### Arquivos
- [`postman/SAP-B1-ServiceLayer.postman_collection.json`](./postman/SAP-B1-ServiceLayer.postman_collection.json) — Collection do Postman
- [`postman/SAP-B1-ServiceLayer.postman_environment.json`](./postman/SAP-B1-ServiceLayer.postman_environment.json) — Environment do Postman
- [`insomnia/SAP-B1-ServiceLayer.insomnia_collection.json`](./insomnia/SAP-B1-ServiceLayer.insomnia_collection.json) — Collection nativa do Insomnia + environment

### Início Rápido (3 passos)
1. **Importe** o(s) arquivo(s) JSON no Postman (`File → Import`) ou no Insomnia (`Import Data`).
2. **Selecione** o ambiente `SAP B1 Service Layer` e configure:
   - `baseUrl` → ex: `https://your-server:50000/b1s/v2`
   - `UserName`, `Password`, `CompanyDB`
3. **Execute `00 - Authentication → Login`** uma vez. O script de teste / tags nativas guardam o `B1SESSION` e o `ROUTEID` — todas as outras requisições agora estão autenticadas.

> 💡 Se o seu servidor SAP B1 usar um certificado auto-assinado (self-signed), desative a verificação de certificado SSL no Postman (`Settings → General → SSL certificate verification = OFF`) ou nas preferências do Insomnia.

### Exemplos de serviços cobertos
`BusinessPartners`, `Items`, `Orders`, `Quotations`, `DeliveryNotes`, `Invoices`, `CreditNotes`, `PurchaseOrders`, `PurchaseInvoices`, `JournalEntries`, `ChartOfAccounts`, `Warehouses`, `PriceLists`, `Employees`, `Activities`, `Attachments2`, `BankPages`, `Projects`, `SalesPersons`, e **mais de 480 outros** — todas as entidades e métodos de serviço expostos pelo SAP B1 Service Layer.

## Estrutura do Repositório

- **/postman**: Contém a collection e environment prontos para importar no Postman.
- **/insomnia**: Contém a collection unificada (endpoints + ambiente) pronta para importar nativamente no Insomnia.
- **/services**: Contém arquivos JSON para cada serviço, detalhando endpoints, operações e exemplos (ex: `AccountCategoryService.json`).
- **/schemas**: Inclui arquivos EDMX do OData V4 definindo os metadados para cada serviço.
- **/examples**: Fornece códigos de amostra e exemplos de chamadas de API para diferentes serviços e operações.
- **/guides**: Tutoriais amigáveis para iniciantes e instruções de configuração para trabalhar com o SAP B1 Service Layer.

## Começando

### Pré-requisitos
Para usar as APIs do SAP B1 Service Layer, certifique-se de ter:
- Acesso a uma instância do SAP B1 com o Service Layer habilitado.
- Uma conta de usuário válida com as permissões apropriadas.
- Um ambiente de desenvolvimento com ferramentas como Postman, cURL, ou uma linguagem de programação (ex: Python, JavaScript) para fazer requisições HTTP.
- Entendimento básico sobre APIs REST e OData V4.

### Instruções de Configuração
1. **Acesso ao Service Layer**:
   - O SAP B1 Service Layer geralmente é hospedado em uma URL como `https://<your-server>:50000/b1s/v2/`.
   - Faça login no Service Layer usando uma requisição POST para o endpoint `/Login` com suas credenciais:
     ```json
     POST https://<your-server>:50000/b1s/v2/Login
     {
       "UserName": "your-username",
       "Password": "your-password",
       "CompanyDB": "your-company-database"
     }
     ```
     Salve o `SessionId` da resposta para requisições subsequentes.

2. **Explore os Serviços Disponíveis**:
   - O Service Layer expõe vários serviços como `AccountCategoryService`, `BusinessPartners`, e mais.
   - Consulte os arquivos JSON na pasta `/services` para detalhes sobre cada serviço e suas operações.

3. **Use Esquemas de Metadados**:
   - A pasta `/schemas` contém arquivos EDMX que descrevem os modelos de dados para cada serviço.
   - Use estes schemas para entender a estrutura de entidades e enumerações usadas nas respostas da API.

4. **Teste Chamadas de API**:
   - Use ferramentas como Postman ou cURL para testar os endpoints da API.
   - Exemplos de requisições são fornecidos na pasta `/examples` e dentro dos arquivos JSON em `/services`.

## Serviços e Endpoints

A pasta `/services` contém arquivos JSON que descrevem os serviços disponíveis e suas operações. Abaixo está um exemplo do `AccountCategoryService` baseado em sua definição JSON:

### AccountCategoryService
**Descrição**: Esta API permite que você invoque as interfaces definidas no `AccountCategoryService`, que gerencia as categorias de conta no SAP B1.

**Operações**:
- **Get Category List**:
  - **Method**: GET
  - **Path**: `AccountCategoryService_GetCategoryList`
  - **Descrição**: Recupera uma lista de categorias de conta.
  - **Exemplo**:
    ```
    GET https://<your-server>:50000/b1s/v2/AccountCategoryService_GetCategoryList
    ```
  - **Method**: POST
  - **Path**: `AccountCategoryService_GetCategoryList`
  - **Descrição**: Invoca o método `GetCategoryList` para recuperar as categorias de conta.
  - **Exemplo**:
    ```
    POST https://<your-server>:50000/b1s/v2/AccountCategoryService_GetCategoryList
    ```

Para uma lista completa dos serviços e suas operações, consulte os arquivos JSON na pasta `/services`.

## Esquemas de Metadados

O Service Layer usa OData V4 para definir seus modelos de dados. A pasta `/schemas` contém arquivos EDMX que descrevem a estrutura de entidades e enumerações. Abaixo está um trecho de exemplo do schema para o `AccountCategoryService`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<edmx:Edmx Version="4.0" xmlns:edmx="http://docs.oasis-open.org/odata/ns/edmx">
    <edmx:DataServices>
        <Schema Namespace="SAPB1" xmlns="http://docs.oasis-open.org/odata/ns/edm">
            <EnumType IsFlags="false" Name="AccountCategorySourceEnum" UnderlyingType="Edm.Int32">
                <Member Name="acsBalanceSheet" Value="0"/>
                <Member Name="acsProfitAndLoss" Value="1"/>
                <Member Name="acsTrialBalance" Value="2"/>
            </EnumType>
            <EnumType IsFlags="false" Name="AccountSegmentationTypeEnum" UnderlyingType="Edm.Int32">
                <Member Name="ast_Alphanumeric" Value="0"/>
                <Member Name="ast_Numeric" Value="1"/>
            </EnumType>
            <EnumType IsFlags="false" Name="AcquisitionPeriodControlEnum" UnderlyingType="Edm.Int32">
                <Member Name="apcProRataTemporis" Value="0"/>
                <Member Name="apcFirstYearConvention" Value="1"/>
                <Member Name="apcHalfYear" Value="2"/>
                <Member Name="apcFullYear" Value="3"/>
            </EnumType>
            <EnumType IsFlags="false" Name="AcquisitionProRataTypeEnum" UnderlyingType="Edm.Int32">
                <Member Name="aprtExactlyDailyBase" Value="0"/>
                <Member Name="aprtFirstDayOfCurrentPeriod" Value="1"/>
                <Member Name="aprtFirstDayOfNextPeriod" Value="2"/>
            </EnumType>
            <EnumType IsFlags="false" Name="ActivityRecipientObjTypeEnum" UnderlyingType="Edm.Int32">
                <Member Name="arotUser" Value="0"/>
                <Member Name="arotEmployee" Value="1"/>
                <Member Name="arotRecipientList" Value="2"/>
            </EnumType>
        </Schema>
    </edmx:DataServices>
</edmx:Edmx>
```

Este schema define as enumerações usadas pelo `AccountCategoryService`, como `AccountCategorySourceEnum` e `AcquisitionPeriodControlEnum`. Consulte a pasta `/schemas` para schemas adicionais.

## Exemplos

A pasta `/examples` contém chamadas de API de amostra para vários serviços. Abaixo está um exemplo para invocar o endpoint `AccountCategoryService_GetCategoryList`:

```bash
curl -X GET "https://<your-server>:50000/b1s/v2/AccountCategoryService_GetCategoryList" \
-H "Cookie: B1SESSION=<your-session-id>" \
-H "Content-Type: application/json"
```

Exemplos adicionais, incluindo requisições POST e payloads, podem ser encontrados na pasta `/examples` e dentro dos arquivos JSON em `/services`.

## Guias para Iniciantes

A pasta `/guides` contém tutoriais para ajudar novos desenvolvedores a começar com o SAP B1 Service Layer. Os principais tópicos incluem:
- **Configurando a Autenticação**: Como fazer login e gerenciar sessões.
- **Fazendo sua Primeira Chamada de API**: Um guia passo a passo para consultar o Service Layer.
- **Entendendo o OData V4**: Uma introdução aos conceitos do OData e como eles se aplicam ao SAP B1.
- **Solucionando Problemas Comuns**: Dicas para resolver erros como sessões inválidas ou payloads incorretos.

## Contribuindo

Contribuições para o `b1-api-cookbook` são bem-vindas! Para contribuir:
1. Faça um fork do repositório.
2. Crie uma nova branch para suas alterações.
3. Adicione ou atualize arquivos JSON, schemas, ou examples.
4. Envie um pull request com uma descrição clara das suas mudanças.

Por favor, garanta que quaisquer novos arquivos JSON ou schemas estejam precisos e sigam o padrão OData V4.

## Licença

Este repositório está licenciado sob a [Licença MIT](LICENSE). Sinta-se à vontade para usar, modificar e distribuir o conteúdo conforme necessário.

## Contato

Para dúvidas ou feedback, por favor, abra uma issue no repositório ou entre em contato com os mantenedores.