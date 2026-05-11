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

### Objetivo Geral
Desenvolver e implantar a plataforma SaaS B2B ENGER para centralizar e automatizar a gestão de obras, englobando o controle financeiro, a gestão de força de trabalho e a geração de orçamentos profissionais.

### Objetivos Específicos
* Implementar as funcionalidades de assinatura do usuário/empresa, geração de orçamentos, etapas, gestão das obras, validação de admins, o que pode ser utilizado com base no seu nivel de administração.
* Automatizar a geração profissional de orçamentos, controle de obras, etapas, controle financeiro do que foi pago x recebido.
* Integrar um sistema de checkout transparente e de gestão de assinaturas recorrentes utilizando a API do Mercado Pago.
* Garantir uma interface de usuário clara e intuitiva, aplicando formatações amigáveis para facilitar a leitura financeira.

## Stack Tecnológico

A escolha do stack tecnológico foi baseada na necessidade de escalabilidade, segurança e facilidade de manutenção exigidas por um ecossistema corporativo B2B SaaS.

* **Backend - C# (.NET Core):** Linguagem robusta e fortemente tipada, ideal para implementar regras de negócio seguras no sistema financeiro e de gestão. Facilita a adoção de padrões arquiteturais avançados, como Domain-Driven Design (DDD) e Clean Architecture, garantindo o isolamento da lógica de domínio.
* **Frontend - React com Tailwind CSS:** O React viabiliza a criação do construtor de orçamentos interativo de forma componentizada e reativa. O Tailwind CSS foi escolhido para agilizar a estilização da identidade visual corporativa do projeto, baseada em um alto contraste com as cores laranja, preto e branco, suportando nativamente a alternância entre os temas claro (laranja e branco) e escuro (laranja e preto).
* **Banco de Dados - PostgreSQL** Sistemas gerenciadores de banco de dados relacionais escolhidos por sua confiabilidade e integridade para gerenciar as tabelas e por ser open source e o mais utilizado.
* **Infraestrutura e DevOps - Docker, Docker Compose e GitHub Actions:** O Docker garante a padronização dos ambientes de desenvolvimento, orquestrando a API e os bancos de dados simultaneamente. O GitHub Actions foi adotado para compor a esteira de CI/CD, automatizando a execução de testes unitários sempre que novos códigos são enviados para a branch `develop`.

## Descrição da Solução

O ENGER foi concebido como uma plataforma SaaS B2B robusta, desenhada para centralizar a gestão de obras e eliminar a fragmentação de processos administrativos e operacionais no setor da construção civil. A solução organiza-se através de uma arquitetura moderna que separa as responsabilidades de negócio da infraestrutura, garantindo que o sistema seja escalável e de fácil manutenção. No centro da experiência do usuário está o construtor interativo de orçamentos, que permite aos gestores manipular dados de insumos e serviços em tempo real, oferecendo uma interface dinâmica que supera as limitações de visualizações estáticas comuns em sistemas tradicionais.

Para garantir a fluidez dos processos financeiros, o sistema integra-se de forma transparente com a API do Mercado Pago, permitindo o processamento de pagamentos e a gestão de assinaturas recorrentes diretamente pela plataforma. Complementando essa automação, o ENGER utiliza rotinas de background (workers) para a compilação e geração profissional de documentos em PDF, realizando o disparo automático de orçamentos e relatórios por e-mail para os clientes finais. Essa estrutura assíncrona garante que tarefas pesadas de processamento não interfiram na performance da interface do usuário, mantendo a agilidade do sistema mesmo em períodos de alta demanda.

A segurança é um pilar fundamental da organização do sistema, sendo em tokens implementada através de autenticação baseada JWT para proteger as rotas da API e garantir que apenas usuários autorizados acessem os dados sensíveis de cada obra. O frontend entrega uma identidade visual de alto impacto focada no público corporativo, utilizando uma paleta de cores em laranja, preto e branco que se adapta automaticamente aos modos claro e escuro. A preocupação com a usabilidade estende-se à clareza dos dados apresentados, onde informações financeiras e alíquotas são formatadas de maneira limpa (sem casas decimais redundantes) para evitar poluição visual e facilitar a leitura técnica.

## Arquitetura

Este tópico apresenta a organização estrutural do sistema ENGER, detalhando suas camadas e os artefatos gerados durante o processo de desenvolvimento.

A plataforma ENGER adota o padrão arquitetural **Clean Architecture** em conjunto com **Domain-Driven Design (DDD)** no backend. Essa estrutura visa separar as responsabilidades do negócio das camadas de infraestrutura e entrega, garantindo a manutenibilidade e escalabilidade do software. O frontend utiliza **React** e **Tailwind CSS** para construir as interfaces dinâmicas, incluindo o construtor interativo de orçamentos. A persistência de dados é gerenciada por bancos de dados relacionais **PostgreSQL** e **SQL Server**, enquanto tarefas assíncronas, como geração de PDFs e envio de e-mails, são executadas por workers de background.

Ao longo do desenvolvimento do projeto ENGER, foram gerados artefatos técnicos e de planejamento para suportar a solução. Atuando como um guia para a equipe de desenvolvimento e stakeholders, os artefatos específicos criados para este projeto incluem:

1.  **Benchmarking (Tabela Comparativa):** Análise competitiva entre o ENGER e soluções de mercado para identificar diferenciais.
2.  **MVP Canvas:** Definição do produto mínimo viável focado na orçamentação interativa e controle de presença.
3.  **Histórias do Usuário:** Descrição detalhada das funcionalidades sob a perspectiva dos gestores de obras e funcionários.
4.  **Diagrama Entidade-Relacionamento (ER):** Modelagem do banco de dados relacional (PostgreSQL e SQL Server) para o controle de orçamentos, obras e funcionários.
5.  **Protótipos de Interface:** High-fidelity wireframes e mockups do frontend em React, destacando a paleta de cores laranja, preto e branco e o construtor interativo.

*(Adicione aqui o link para o repositório que contém a listagem e os arquivos dos artefatos listados acima).*

**Exemplos de repositórios:**

* [https://github.com/luciano-zanuz/enger-projeto](https://github.com/luciano-zanuz/enger-projeto)

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
