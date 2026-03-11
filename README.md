# 🧪 DESAFIO-QA-BEEDOO-2026

**Aplicação disponível em:** 🔗 [creative-sherbet-a51eac.netlify.app](https://creative-sherbet-a51eac.netlify.app/)

# 📑 Sumário

- [📊 Análise Inicial da Aplicação](#-análise-inicial-da-aplicação)
    - [🎯 Objetivo da Aplicação](#-objetivo-da-aplicação)
    - [🔄 Principais Fluxos Disponíveis](#-principais-fluxos-disponíveis)
    - [⚠️ Pontos Críticos da Aplicação](#️-pontos-críticos-da-aplicação)

- [🧠 Decisões Tomadas para a Criação dos Testes](#-decisões-tomadas-para-a-criação-dos-testes)

- [🧪 Cenários e Casos de Teste](#-cenários-e-casos-de-teste)

- [📄 Relatório de Bugs Encontrados](#-relatório-de-bugs-encontrados)
    - [🐞 Bug 1 - Campos obrigatórios não são validados](#-bug-1---campos-obrigatórios-não-são-validados)
    - [🐞 Bug 2 - Botão de delete não remove o curso cadastrado](#-bug-2---botão-de-delete-não-remove-o-curso-cadastrado)
    - [🐞 Bug 3 - Sistema permite cadastrar curso com datas invertidas](#-bug-3---sistema-permite-cadastrar-curso-com-datas-invertidas)
    - [🐞 Bug 4 - Campo de vagas aceita valores decimais ou negativos](#-bug-4---campo-de-vagas-aceita-valores-decimais-ou-negativos)
    - [🐞 Bug 5 - Campo de quantidade de vagas aceita caracteres alfabéticos e especiais](#-bug-5---campo-de-quantidade-de-vagas-aceita-caracteres-alfabéticos-e-especiais)
    - [🐞 Bug 6 - Stored HTML Injection – Tags HTML são renderizadas na listagem sem sanitização](#-bug-6---stored-html-injection--tags-html-são-renderizadas-na-listagem-sem-sanitização)
    - [🐞 Bug 7 - Página de cadastro apresenta erro 404 ao ser recarregada](#-bug-7---página-de-cadastro-apresenta-erro-404-ao-ser-recarregada)
    - [🐞 Bug 8 - Manipulação de dados no LocalStorage](#-bug-8---manipulação-de-dados-no-localstorage)

- [🔎 Resumo da análise](#-resumo-da-análise)
    - [📈 Indicadores de Qualidade](#-indicadores-de-qualidade)
    - [🎯 Prioridade de Correção](#-prioridade-de-correção)

- [📸 Evidências da Execução dos Testes](#-evidências-da-execução-dos-testes)

- [📊 Estrutura da Documentação na Planilha do Google Sheets](#-estrutura-da-documentação-na-planilha-do-google-sheets)
  - [📋 Aba 1: Capa / Visão Geral](#-aba-1-capa--visão-geral)
  - [🐞 Aba 2: Bugs Encontrados](#-aba-2-bugs-encontrados)
  - [📑 Aba 3: Gherkin - Casos de Teste](#-aba-3-gherkin---casos-de-teste)
  - [✅ Objetivo da organização](#-objetivo-da-organização)

- [⚠️ Pontos de Atenção](#️-pontos-de-atenção)
# 📊 Análise Inicial da Aplicação

## 🎯 Objetivo da Aplicação

A aplicação se trata de um sistema de cadastro de cursos onde é possível inserir informações específicas sobre cada curso e consultar essas informações de maneira individual. Ela permite gerenciar cursos educacionais, com foco em adicionar e listar itens.

## 🔄 Principais Fluxos Disponíveis

- **Cadastro de curso:**  
    Preencher campos como nome, datas de início/fim e número de vagas, e adicionar à base.

- **Listagem de cursos:**  
    Visualizar todos os cursos cadastrados em uma tabela ou lista, com a opção de deletar.

## ⚠️ Pontos Críticos da Aplicação

- **Formatação de dados inseridos:**  
    Datas e números precisam de validação para evitar entradas ilógicas (ex.: datas invertidas ou vagas negativas), pois afetam a integridade e organização dos dados.

- **Organização das informações:**  
    A listagem deve exibir os dados corretamente sem perda de informações (ex.: campos vazios ou tipos errados).

- **Cobrança de informações obrigatórias:**  
    Campos opcionais permitem cadastros vazios, o que pode levar a dados inconsistentes e impactar a usabilidade.

# 🧠 Decisões Tomadas para a Criação dos Testes

Decidi focar em cenários positivos para validar fluxos principais (cadastro e listagem) e negativos para cobrir bugs identificados, como validações falhas. Incluí validações de campos para dados numéricos/datas e fluxos alternativos como `delete`.  

A análise foi feita em **Gherkin** para trazer mais clareza.  

Considerei comportamentos inesperados baseados em exploração, como entradas inválidas que não são bloqueadas.

# 🧪 Cenários e Casos de Teste
Os cenários e casos de teste para o módulo de cursos foram criados com base na análise realizada. Eles incluem:

- Fluxo principal de cadastro de curso;
- Listagem de cursos;
- Cenários negativos;
- Validações de campos;
- Comportamentos inesperados.

# 📄 Relatório de Bugs Encontrados
Abaixo tem o registro de todos os bugs encontrados durante a execução dos testes.  
Cada bug inclui título, passos para reproduzir, resultado atual, resultado esperado e severidade/impacto. Detalhes completos na planilha a baixo juntamente com registros visuais de cada bug.

## 🐞 Bug 1 - Campos obrigatórios não são validados

🔗 O bug pode ser visualizado em: [Bug 1 - Google Drive](https://drive.google.com/file/d/1TzD4dZTzHK1ogyO9qXj3C8UzuvSA2jPP/view?usp=drive_link).


**Passos para Reproduzir:**  
1. Acesse página de cadastro.  
2. Deixe todos os campos vazios.  
3. Clique em "Cadastrar Curso".

**Resultado Atual:** Um curso com todos os campos vazios é adicionado à listagem, sem qualquer validação ou mensagem de erro.

**Resultado Esperado:** O sistema deve validar os campos obrigatórios, exibir mensagens de erro e impedir o cadastro vazio.

**Consequência:** Afeta integridade dos dados e usabilidade.

<div>
<b>Impacto:</b> 🔴 Alto
<div style="width:220px;background:#ffffff;border-radius:6px;">
<div style="width:100%;background:#e53935;height:10px;border-radius:6px;"></div>
</div>
</div>

## 🐞 Bug 2 - Botão de delete não remove o curso cadastrado

🔗 O bug pode ser visualizado em: [Bug 2 - Google Drive](https://drive.google.com/file/d/14SEtnemeouLqgIYPzqEKJD8wHo_ey0Mo/view?usp=drive_link).

**Passos para Reproduzir:**  
1. Cadastre um novo curso no sistema.  
2. Acesse a lista de cursos cadastrados.  
3. Clique no botão "Excluir Curso" no curso criado.

**Resultado Atual:** O sistema exibe uma mensagem indicando que o curso foi deletado, porém o curso permanece listado na página.

**Resultado Esperado:** O curso deveria ser removido da lista após a ação de exclusão.

**Consequência:** Impede a remoção de registros e compromete o gerenciamento dos cursos.

<div>
<b>Impacto:</b> 🔴 Alto
<div style="width:220px;background:#ffffff;border-radius:6px;">
<div style="width:100%;background:#e53935;height:10px;border-radius:6px;"></div>
</div>
</div>

## 🐞 Bug 3 - Sistema permite cadastrar curso com datas invertidas

🔗 O bug pode ser visualizado em: [Bug 3 - Google Drive](https://drive.google.com/file/d/10VduxPQNCbQYOT9ckWzH35M2WDHKYgj-/view?usp=drive_link).

**Passos para Reproduzir:**  
1. Acesse a página de cadastro de curso.  
2. Insira uma data de início posterior à data de término.  
    - **Início:** `2026-11-30`  
    - **Fim:** `2022-11-30`
3. Clique em "Cadastrar Curso".

**Resultado Atual:** O curso é cadastrado normalmente mesmo com datas inconsistentes.

**Resultado Esperado:** O sistema deve validar as datas e impedir que a data de início seja posterior à data de término.

**Consequência:** Permite cadastro de cursos com períodos inválidos, causando inconsistência nos dados.

<div>
<b>Impacto:</b> 🟡 Médio
<div style="width:220px;background:#ffffff;border-radius:6px;">
<div style="width:50%;background:#fbc02d;height:10px;border-radius:6px;"></div>
</div>
</div>

## 🐞 Bug 4 - Campo de vagas aceita valores decimais ou negativos

🔗 O bug pode ser visualizado em: [Bug 4 - Google Drive](https://drive.google.com/file/d/1_u5otitgSrMU8iVZ8VWL46Tp79BlU3N0/view?usp=drive_link).

**Passos para Reproduzir:**  
1. Acesse a página de cadastro de curso.  
2. No campo de vagas, insira valores inválidos como: `100.5` ou `-100`.
3. Clique em "Cadastrar Curso".

**Resultado Atual:** O sistema aceita os valores e permite o cadastro do curso.

**Resultado Esperado:** O campo de vagas deve aceitar apenas números inteiros positivos.

**Consequência:** Permite cadastro de valores inconsistentes para a quantidade de vagas.

<div>
<b>Impacto:</b> 🟡 Médio
<div style="width:220px;background:#ffffff;border-radius:6px;">
<div style="width:50%;background:#fbc02d;height:10px;border-radius:6px;"></div>
</div>
</div>

## 🐞 Bug 5 - Campo de quantidade de vagas aceita caracteres alfabéticos e especiais

🔗 O bug pode ser visualizado em: [Bug 5 - Google Drive](https://drive.google.com/file/d/1fRPNz7VhgjzeCvVicsAa3PaZeFPi4yex/view?usp=drive_link).

**Passos para Reproduzir:**  
1. Acesse a página de cadastro de curso.  
2. No campo de vagas, insira texto alfabético ou alfanumérico, por exemplo: `abc`, `abc123` ou `abc#123`.
3. Clique em "Cadastrar Curso".

**Resultado Atual:** O curso é cadastrado, porém o campo de vagas fica vazio, sem exibir o valor inserido.

**Resultado Esperado:** O sistema deve impedir a inserção de caracteres inválidos e exibir uma mensagem de erro ao usuário.

**Consequência:** Permite cadastro de cursos com informações incompletas ou inconsistentes.

<div>
<b>Impacto:</b> 🟡 Médio
<div style="width:220px;background:#eee;border-radius:6px;">
<div style="width:50%;background:#fbc02d;height:10px;border-radius:6px;"></div>
</div>
</div>

## 🐞 Bug 6 - Stored HTML Injection – Tags HTML são renderizadas na listagem sem sanitização

🔗 O bug pode ser visualizado em: [Bug 6 - Google Drive](https://drive.google.com/file/d/1V56Z1XrqaBMOO3zbg4ZtlyrC-M3O1o4Y/view?usp=sharing).

**Passos para Reproduzir:**  
1. Acesse a página de cadastro de cursos.  
2. No campo "Nome do Curso", insira um payload HTML, por exemplo:  
   - `<b>negrito</b>` (para testar renderização simples)  
   - `<img src=x onerror=alert(1)>` (para testar potencial XSS)  
   - `<script>alert(1)</script>` (para confirmar bloqueio de script)  
3. Preencha os outros campos com valores válidos (datas e vagas).  
4. Clique em "Cadastrar Curso" e volte para a página de listagem.  
5. Observe o nome do curso na tabela da listagem.

**Resultado Atual:** Tags HTML simples são renderizadas diretamente na listagem (ex.: negrito aparece em negrito). Payloads com atributos de evento (ex.: onerror) ou tags `<script>` não executam JavaScript (provavelmente devido a CSP), mas resultam em artefatos visuais estranhos, como texto vazado (ex.: 'creative-sherbet-a51eac.netlify.app/ 1 OK') ou elementos quebrados na tela. O conteúdo injetado persiste no localStorage, afetando a visualização para qualquer usuário que acesse a listagem.

**Resultado Esperado:** O sistema deve sanitizar todas as entradas de usuário, tratando-as como texto plano (ex.: escapando caracteres especiais como <b>negrito</b>) ou rejeitando inputs com tags HTML. Nenhuma tag deve ser renderizada ou causar alterações visuais indesejadas, garantindo integridade da UI.

**Consequência:** Gravidade alta devido ao defacement persistente via localStorage, que compromete a usabilidade e integridade visual da aplicação para todos os acessos subsequentes. Embora não execute JS, representa risco de escalada em ambientes sem CSP rigoroso.

<div>
<b>Impacto:</b> 🔴 Alto
<div style="width:220px;background:#eee;border-radius:6px;">
<div style="width:100%;background:#e53935;height:10px;border-radius:6px;"></div>
</div>
</div>


## 🐞 Bug 7 - Página de cadastro apresenta erro 404 ao ser recarregada

🔗 O bug pode ser visualizado em: [Bug 7 - Google Drive](https://drive.google.com/file/d/1jJOnrRYyK64qjFQijVHPHhAr4U6tYnRv/view?usp=sharing).

**Passos para Reproduzir:**  
1. Acesse a página inicial da aplicação: [https://creative-sherbet-a51eac.netlify.app/](https://creative-sherbet-a51eac.netlify.app/)  
2. Clique no botão "Cadastrar Curso" para acessar a página `https://creative-sherbet-a51eac.netlify.app/new-course`  
3. Com a página de cadastro carregada, pressione **F5** ou clique no botão de recarregar do navegador  
4. Observe o resultado

**Resultado Atual:** Ao recarregar a página `/new-course`, o navegador exibe uma mensagem de erro **404 - Página não encontrada**. A aplicação não consegue recarregar a rota diretamente, exigindo que o usuário volte manualmente para a página inicial (`/`) para voltar a usar o sistema.

**Resultado Esperado:** A página de cadastro deveria ser recarregada normalmente, mantendo o estado e permitindo que o usuário continue preenchendo os campos ou visualize o formulário corretamente, sem apresentar erro 404.

**Consequência:** Impede que usuários compartilhem o link direto da página de cadastro, causa frustração ao usuário que tenta recarregar a página durante o preenchimento do formulário, indica possível problema de configuração de rotas no front-end (provavelmente aplicação SPA sem tratamento adequado de rotas no servidor), compromete a experiência do usuário e a confiabilidade da aplicação.

<div>
<b>Impacto:</b> 🟡 Médio
<div style="width:220px;background:#eee;border-radius:6px;">
<div style="width:50%;background:#fbc02d;height:10px;border-radius:6px;"></div>
</div>
</div>

## 🐞 Bug 8 - Manipulação de dados no LocalStorage

🔗 O bug pode ser visualizado em: [Bug 8 - Google Drive](https://drive.google.com/file/d/1Fs9tn9QXzNAyjMbBpC5sCUAcpWD4Hs6x/view?usp=sharing).

**Passos para reproduzir:**  
1. Cadastre um curso qualquer.
2. Abra o DevTools (`F12`) > Aba **Application** > **Local Storage**.
3. Localize a chave onde os cursos estão salvos.
4. Altere o valor de um campo (ex: mude "Vagas: 10" para "Vagas: 9999").
5. Recarregue a página (F5).

**Resultado Atual:** A interface exibe os dados alterados manualmente sem qualquer verificação de integridade.

**Resultado Esperado:** O sistema deve validar a integridade dos dados locais ou, idealmente, buscar a "fonte da verdade" de um banco de dados seguro que não permita manipulação via console.

**Consequência:** É possível alterar manualmente os valores das chaves no `localStorage` (como nomes de cursos, vagas ou datas) e a aplicação renderiza essas alterações após o refresh, permitindo a exibição de dados falsos ou corrompidos.

<div style="margin-bottom: 20px;">
<b>Impacto:</b> 🔴 Alto
<div style="width:220px;background:#eee;border-radius:6px;">
<div style="width:100%;background:#e53935;height:10px;border-radius:6px;"></div>
</div>
</div>

# 🔎 Resumo da análise
Durante a execução dos testes foi realizada uma análise exploratória da aplicação, com o objetivo de validar o funcionamento das principais funcionalidades, identificar cenários de erro e verificar a consistência das validações de entrada.  

A tabela abaixo apresenta um resumo da quantidade de cenários testados em cada categoria, bem como uma estimativa da cobertura obtida durante a análise.

## 📈 Indicadores de Qualidade

| Métrica                     | Valor |
| --------------------------- | ----- |
| ✅ Testes Bem-Sucedidos     | 3     |
| ❌ Testes com Falha         | 8     |
| 🐞 Total de Bugs            | 8     |
| 🔴 Bugs de Alta Severidade  | 4     |
| 🟡 Bugs de Média Severidade | 4     |

## 🎯 Prioridade de Correção

| Prioridade | Bugs                           | Impacto                                                  |
| ---------- | ------------------------------ | -------------------------------------------------------- |
| 🔴 Alta    | BUG-01, BUG-02, BUG-06, BUG-08 | Impedem funcionalidades básicas ou comprometem segurança |
| 🟡 Média   | BUG-03, BUG-04, BUG-05, BUG-07 | Afetam integridade dos dados                             |

## 📸 Evidências da Execução dos Testes
As evidências dos testes executados estão armazenadas em uma pasta compartilhada no Google Drive: [Evidências - Google Drive](https://drive.google.com/drive/folders/1jLYwNlf3WtTswnoayn3wq9dtdsRjJd_p?usp=sharing).

## 📊 Estrutura da Documentação na Planilha do Google Sheets

A planilha completa está disponível no link: [Casos de Testes - Google Sheets](https://docs.google.com/spreadsheets/d/1nm8IFBsmV1RylupdeKat3SpsVn1AfsGd1DzzUP-IXss/edit?usp=sharing)

Para facilitar a navegação e consulta, organizei a documentação em **3 abas**, cada uma com um propósito específico:

### 📋 **Aba 1: Capa / Visão Geral**
Aba inicial com as **informações gerais do projeto de testes**, funcionando como uma capa executiva.

| Item                            | Conteúdo                                                                                                          |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Nome do Projeto**             | DESAFIO-QA-BEEDOO-2026                                                                                            |
| **Módulo testado**              | Cadastro e Listagem de Cursos                                                                                     |
| **URL da aplicação**            | [creative-sherbet-a51eac.netlify.app](https://creative-sherbet-a51eac.netlify.app/)                               |
| **Data de criação dos testes**  | 2026-03-09                                                                                                        |
| **Responsável**                 | Alvani Miguel                                                                                                     |
| **Navegador**                   | Firefox                                                                                                           |
| **Sistema Operacional**         | Fedora 43 - Linux 6.18.13-200.fc43.x86_64                                                                         |
| **Link do repositório GitHub**  | [github.com/alvanimiguel/DESAFIO-QA-BEEDOO-2026](https://github.com/alvanimiguel/DESAFIO-QA-BEEDOO-2026)          |
| **Link da pasta de evidências** | [Evidências - Google Drive](https://drive.google.com/drive/folders/1jLYwNlf3WtTswnoayn3wq9dtdsRjJd_p?usp=sharing) |
| **Total de cenários criados**   | 11                                                                                                                 |
| **Total de casos de teste**     | 11                                                                                                                 |

### 🐞 **Aba 2: Bugs Encontrados**
Esta aba reúne todos os **8 bugs identificados** durante a execução dos testes, com detalhamento completo para facilitar a reprodução e correção.

| Coluna                        | Descrição                                 |
| ----------------------------- |------------------------------------------ |
| **ID Bug**                    | Identificador único (BUG-01 a BUG-08)     |
| **Título do Bug**             | Descrição resumida e objetiva do problema |
| **Severidade**                | Impacto no sistema (Alta/Média)           |
| **Prioridade**                | Urgência para correção (Alta/Média)       |
| **Status**                    | Aberto ou Resolvido                       |
| **Caso de Teste relacionado** | Vínculo com o CT que originou o bug       |
| **Passos para Reproduzir**    | Sequência detalhada para replicar o erro  |
| **Resultado Atual**           | Comportamento observado (o bug)           |
| **Resultado Esperado**        | Comportamento correto que deveria ocorrer |
| **Evidência**                 | Link para comprovação visual do bug       |

### 📑 **Aba 3: Gherkin - Casos de Teste**
Nesta aba estão documentados todos os **11 cenários de teste** criados para a validação do módulo de cadastro e listagem de cursos.

| Coluna                     | Descrição                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------ |
| **ID**                     | Identificador único do caso de teste                                                 |
| **Cenário/Funcionalidade** | Descrição clara do que está sendo testado                                            |
| **Tipo**                   | Classificação entre Positivo (funcionamento correto) e Negativo (validações e erros) |
| **Pré-condição**           | Estado necessário para executar o teste                                              |
| **Passos (Gherkin)**       | Cenário escrito no formato DADO/QUANDO/ENTÃO para melhor legibilidade                |
| **Resultado Esperado**     | Comportamento esperado do sistema                                                    |
| **Prioridade**             | Alta, Média ou Baixa                                                                 |
| **Status**                 | OK (passou) ok Falha (bug encontrado)                                                |
| **Evidência**              | Link direto para o print ou vídeo comprovando o resultado                            |
| **Observação**             | Informações complementares sobre o cenário                                           |

### ✅ Objetivo da organização

| Aba            | Objetivo                        | Para quem é                  |
| -------------- | ------------------------------- | ---------------------------  |
| 📑 **Gherkin** | Documentar o que foi testado    | Time de QA e Desenvolvimento |
| 🐞 **Bugs**    | Registrar problemas encontrados | Gestores e Desenvolvedores   |
| 📋 **Capa**    | Visão executiva do projeto      | Stakeholders e Recrutadores  |

Essa estrutura permite que diferentes públicos encontrem rapidamente as informações relevantes, desde a visão macro até os detalhes técnicos de cada bug e caso de teste.

# ⚠️ Pontos de Atenção
- Os testes priorizaram validações de entrada de dados e integridade das informações.
- Foram executados testes exploratórios para identificar comportamentos inesperados.
- A cobertura inclui fluxos principais, cenários negativos e validações de regras de negócio.
