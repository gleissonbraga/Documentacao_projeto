# Documentação do Projeto: ENGER

## Resumo do Projeto

A gestão de obras na construção civil frequentemente enfrenta desafios ligados à fragmentação de processos operacionais e administrativos. Essa desintegração dificulta o acompanhamento da presença da força de trabalho e gera ineficiências na elaboração, envio e cobrança de orçamentos. Para solucionar essas lacunas, este trabalho apresenta o ENGER, uma plataforma SaaS B2B que centraliza a gestão da construção através de ferramentas integradas, destacando-se um construtor interativo de orçamentos e a automatização de comunicações e pagamentos. Como consequência, a solução otimiza o fluxo de trabalho das empresas do setor, garantindo maior previsibilidade financeira e um controle abrangente sobre o ciclo de vida e os custos operacionais de cada obra.

## Definição do Problema

O setor de construção civil demanda um controle rigoroso de insumos, mão de obra e fluxo de caixa. Atualmente, muitas empresas gerenciam essas etapas de forma isolada, utilizando planilhas genéricas ou sistemas que apenas exibem dados de forma estática, sem permitir uma interação ágil com a construção do orçamento. 

Isso gera gargalos significativos em duas frentes principais:
1. **Controle de Mão de Obra e Custos:** A ausência de um sistema unificado para gerenciar a presença dos funcionários nas obras resulta em falhas no cálculo de custos reais e dificuldades no fechamento da folha e do orçamento final.
2. **Comunicação e Cobrança:** O processo de elaboração, envio de orçamentos para o cliente e a gestão de recebimentos ou assinaturas recorrentes costuma ser fragmentado e manual. Isso aumenta a inadimplência, eleva o tempo de resposta ao cliente e prejudica a experiência do usuário final.

O ENGER surge para resolver esses problemas, oferecendo um ambiente unificado de gestão B2B voltado para a praticidade e a automação de rotinas da construção civil.

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
