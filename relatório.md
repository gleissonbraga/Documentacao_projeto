# Documentação do Projeto: ENGER

## Resumo do Projeto

A ideia é desenvolver um projeto SaaS de Gestão de Obras voltado para pequenas, médias e grandes empresa aonde o MVP irá entregar toda a parte de geração e orçamentos, gestão da obra, com funcionários envolvidos, preços, valores quitados, etapas da obra e como se encontra, validar se esta em atraso, etapas concluidas sem atraso e também os valores pagos das etapas concluidas.

Isso gera gargalos significativos em duas frentes principais:
1. **Controle de Mão de Obra e Custos:** Controle de obras, valores Recebidos x Gastos, atraso de obra, o porquê ela atrasou, guardas os processos como garantia de executado com fotos e documentações e deixando a parte escrita e cansativ, como envio de orçamento em caderno.
2. **Por que é um problema:** É um problema para empresas de pequeno, médio e grande porte não terem dados de suas obras, aonde ele consegue vaslidar estruturar e buscar ter uma acertividade em orçamento, etapas para uma conclusão e gestão da obra.
3. **A solução:** Para solucionar essas lacunas, este trabalho apresenta o ENGER, uma plataforma SaaS B2B que centraliza a gestão da construção através de um construtor interativo de orçamentos e da automatização de rotinas financeiras e comunicações.
4. **A consequência:** Como consequência, o sistema otimiza o fluxo de trabalho das empresas do setor, garantindo maior previsibilidade financeira e um controle centralizado sobre os custos de cada obra e previsão de tempo, o que foi feito/construido para abordar em próximas obras.

## Definição do Problema

O setor da construção civil é caracterizado por uma alta complexidade logística e financeira, exigindo um rigoroso acompanhamento de custos, prazos e recursos humanos. Contudo, a digitalização dos processos de gestão de obras ainda é um desafio. Segundo Mattos (2010, p. 45), o planejamento e o controle orçamentário são frequentemente negligenciados ou executados de maneira rudimentar, resultando em estouros de orçamento e atrasos significativos na entrega dos projetos.

A gestão operacional de um canteiro de obras envolve múltiplas frentes que, quando tratadas de forma isolada, geram gargalos administrativos. Durante a etapa de *discovery* do projeto ENGER — que incluiu a análise de requisitos técnicos e fluxos de trabalho baseados em instâncias de banco de dados e operações de um ambiente real de supervisão técnica —, constatou-se que a fragmentação da informação é a principal dor enfrentada pelos gestores. 

As dificuldades vivenciadas no contexto real de administração de obras que motivaram o desenvolvimento deste projeto incluem:

1. **Falta de Praticidade e Usabilidade na Orçamentação:** A elaboração de orçamentos é o coração financeiro da obra. Identificou-se que muitos sistemas fornecem apenas telas estáticas de visualização de dados. O usuário necessita de um construtor de orçamentos interativo, onde seja possível manipular variáveis, aplicar formatações de interface claras (como a exibição limpa de decimais em alíquotas, evitando zeros à direita) e construir o preço final em tempo real, eliminando o uso paralelo de planilhas de rascunho.
2. **Processos Manuais Não Informatizados:** A etapa de formalização comercial apresenta forte lentidão. A compilação de propostas orçamentárias e o envio para os clientes finais são, na maioria das vezes, processos executados manualmente. Além disso, a gestão de assinaturas e o processo de cobrança carecem de automação sistêmica, aumentando a inadimplência e o trabalho administrativo recorrente.
3. **Controle de Força de Trabalho:** O rastreamento de presença de funcionários alocados especificamente por obra costuma ser feito em controles paralelos, desconexos do sistema financeiro principal, dificultando o cálculo ágil do custo real da mão de obra.

### Análise de Projetos Correlatos

Para embasar a proposta de valor do ENGER, foi realizada uma pesquisa sobre as ferramentas atualmente utilizadas no nicho de gestão de obras. O mercado divide-se majoritariamente entre soluções genéricas de baixo custo (planilhas) e sistemas ERP engessados.

A Tabela 1 apresenta um comparativo entre as soluções convencionais e o projeto proposto.

**Tabela 1: Comparativo de Funcionalidades entre Projetos Correlatos e o ENGER**

| Funcionalidade / Requisito | Planilhas Eletrônicas (Ex: Excel) | ERPs Tradicionais de Engenharia | Plataforma ENGER |
| :--- | :---: | :---: | :---: |
| **Construtor Interativo de Orçamentos** | Parcial (Requer fórmulas manuais) | Não (Geralmente telas estáticas) | **Sim (Manipulação em tempo real)** |
| **Controle de Presença por Obra** | Não | Sim | **Sim** |
| **Automação de Envio de Orçamentos (PDF)** | Não | Parcial (Requer disparo manual) | **Sim (via Background Workers)** |
| **Checkout Transparente e Assinaturas** | Não | Raro (Dependem de boletos avulsos) | **Sim (Integração de Pagamento)** |
| **Acessibilidade e Modelo de Distribuição** | Arquivo Local / Nuvem Básica | Instalação Local (Desktop) ou Nuvem | **SaaS B2B 100% Web** |

Diante deste cenário comparativo, o desenvolvimento do ENGER justifica-se pela necessidade de preencher a lacuna entre a usabilidade moderna e a automação de processos operacionais e financeiros. O sistema propõe-se a eliminar a fragmentação ao unir o controle da execução da obra com a fluidez na negociação comercial, entregando uma ferramenta SaaS adaptada às necessidades dinâmicas e às dificuldades reais enfrentadas por clientes na construção civil.

## Objetivos

### Objetivo Geral
Desenvolver e implantar a plataforma SaaS B2B ENGER para centralizar e automatizar a gestão de obras, englobando o controle financeiro, a gestão de força de trabalho e a geração de orçamentos profissionais.

### Objetivos Específicos
* Desenvolver um construtor de orçamentos interativo, substituindo telas de visualização estática por uma interface de manipulação de dados de construção em tempo real.
* Implementar o rastreamento e controle de presença de funcionários alocados por obra.
* Automatizar a geração profissional de orçamentos em PDF e seu envio assíncrono para clientes através de workers de background por e-mail.
* Integrar um sistema de checkout transparente e de gestão de assinaturas recorrentes utilizando a API do Mercado Pago.
* Garantir uma interface de usuário clara e intuitiva, aplicando formatações amigáveis (como a remoção de zeros desnecessários em alíquotas e decimais) para facilitar a leitura financeira.

## Stack Tecnológico

A escolha do stack tecnológico foi baseada na necessidade de escalabilidade, segurança e facilidade de manutenção exigidas por um ecossistema corporativo B2B SaaS.

* **Backend - C# (.NET Core):** Linguagem robusta e fortemente tipada, ideal para implementar regras de negócio seguras no sistema financeiro e de gestão. Facilita a adoção de padrões arquiteturais avançados, como Domain-Driven Design (DDD) e Clean Architecture, garantindo o isolamento da lógica de domínio.
* **Frontend - React com Tailwind CSS:** O React viabiliza a criação do construtor de orçamentos interativo de forma componentizada e reativa. O Tailwind CSS foi escolhido para agilizar a estilização da identidade visual corporativa do projeto, baseada em um alto contraste com as cores laranja, preto e branco, suportando nativamente a alternância entre os temas claro (laranja e branco) e escuro (laranja e preto).
* **Banco de Dados - PostgreSQL e SQL Server:** Sistemas gerenciadores de banco de dados relacionais escolhidos por sua confiabilidade e integridade para gerenciar as tabelas de controle financeiro, usuários e obras.
* **Infraestrutura e DevOps - Docker, Docker Compose e GitHub Actions:** O Docker garante a padronização dos ambientes de desenvolvimento, orquestrando a API e os bancos de dados simultaneamente. O GitHub Actions foi adotado para compor a esteira de CI/CD, automatizando a execução de testes unitários sempre que novos códigos são enviados para a branch `develop`.

## Descrição da Solução

O ENGER é uma plataforma SaaS B2B desenhada para atender empresas do setor da construção civil com foco em produtividade. O sistema opera em uma arquitetura baseada em serviços e processos assíncronos. 

Na interface do usuário, destaca-se o construtor de orçamentos, uma tela altamente interativa onde os gestores podem precificar materiais e serviços dinamicamente. O frontend apresenta uma identidade visual corporativa (laranja, preto e branco) limpa, onde valores e alíquotas são formatados com precisão, sem decimais redundantes, facilitando a tomada de decisão.

No backend, a solução integra-se à API do Mercado Pago para realizar a tokenização de cartões e gerenciar rotas de pré-aprovação de pagamentos e assinaturas recorrentes. Além disso, o sistema conta com rotinas de background dedicadas: workers que utilizam bibliotecas de geração de PDF para compilar os relatórios de orçamento construídos na plataforma e dispará-los automaticamente por e-mail para os clientes.

## Arquitetura

O ENGER adota o padrão **Domain-Driven Design (DDD)** aliado aos conceitos de **Clean Architecture**, isolando as regras de negócio de construção e orçamento das camadas de infraestrutura, banco de dados e entrega da API. A autenticação e segurança de acessos são gerenciadas via tokens JWT.

Artefatos gerados para o projeto:
1. **Diagrama Entidade-Relacionamento (ER):** Modelagem estrutural das tabelas de obras, controle de presença de funcionários, orçamentos e faturamento.
2. **Wireframes e Protótipos:** Design das interfaces nos modos claro e escuro, detalhando a usabilidade do construtor interativo de orçamentos.
3. **Documentação de CI/CD:** Arquivos de workflow do GitHub Actions detalhando as etapas de automação e testes na branch `develop`.
4. **Casos de Uso e Fluxogramas:** Mapeamento das rotinas de integração de checkout transparente com o Mercado Pago e o fluxo de envio de e-mails em background.
5. **Configuração de Infraestrutura:** Scripts `Dockerfile` e arquivos `docker-compose.yml` responsáveis pela orquestração local dos serviços.

*(Nota: Adicione aqui o link para o seu repositório no GitHub).*

## Validação

### Estratégia
A validação das regras de negócio estruturais tem sido realizada através de homologação contínua, baseando-se em dumps de banco de dados e especificações providenciadas pela supervisão técnica do projeto. Além disso, os fluxos de CI/CD garantem que as lógicas core do sistema sejam validadas por meio de testes unitários a cada nova integração. O construtor interativo de orçamentos e as diretrizes de design visual (paleta de cores e formatação de dados) foram iterados e validados através de feedbacks diretos sobre a interface.

### Consolidação dos Dados Coletados
*(Nesta seção, futuramente, inclua gráficos de desempenho da API, relatórios do GitHub Actions sobre o sucesso dos testes, ou tabelas com feedbacks e métricas de usabilidade colhidas com usuários de teste).*

## Conclusões
O desenvolvimento do ENGER demonstra a viabilidade de simplificar processos complexos da construção civil — como a alocação de mão de obra e a elaboração técnica de orçamentos — através de uma plataforma SaaS unificada. A escolha por DDD e Clean Architecture permitiu a construção de um back-end escalável, preparado para integrações financeiras, enquanto a adoção de um construtor de orçamentos dinâmico resultou em uma ferramenta de alto valor prático para o gerenciamento de obras.

**Limitações do Projeto e Perspectivas Futuras:**
*(Discuta aqui potenciais expansões, como a criação de aplicativos móveis para apontamento de presença diretamente no canteiro de obras, novas integrações de pagamento ou módulos adicionais).*

## Referências Bibliográficas
*(Adicione aqui as referências técnicas de documentações usadas, como a documentação oficial do C# .NET Core, React, Tailwind CSS, API do Mercado Pago, Docker, etc).*
