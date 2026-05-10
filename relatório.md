# Documentação do Projeto: ENGER

## Resumo do Projeto

A gestão de obras na construção civil frequentemente enfrenta desafios ligados à fragmentação de processos operacionais e administrativos. Essa desintegração dificulta o acompanhamento da presença da força de trabalho, gera ineficiências financeiras e complica o cumprimento de obrigações tributárias rigorosas, como a emissão dos blocos H e K do SPED fiscal. Para solucionar essas lacunas, este trabalho apresenta o ENGER, uma plataforma SaaS B2B que centraliza a gestão da construção através de ferramentas integradas, destacando-se um construtor interativo de orçamentos e a automatização de relatórios e cobranças. Como consequência, a solução otimiza o fluxo de trabalho das empresas do setor, garantindo maior precisão na conformidade tributária e um controle abrangente sobre o ciclo de vida e custos de cada obra.

## Definição do Problema

O setor de construção civil demanda um controle rigoroso de insumos, mão de obra e conformidade fiscal. Atualmente, muitas empresas gerenciam essas etapas de forma isolada, utilizando planilhas genéricas ou sistemas que apenas exibem dados de forma estática, sem permitir uma interação real com a construção do orçamento. 

Isso gera gargalos significativos em três frentes principais:
1. **Controle de Mão de Obra e Custos:** A ausência de um sistema unificado para gerenciar a presença dos funcionários nas obras resulta em falhas no cálculo de custos reais.
2. **Complexidade Fiscal:** A legislação tributária exige relatórios precisos, como os blocos H e K do SPED. Sistemas genéricos frequentemente falham na validação de CST/CFOP e na manutenção de códigos específicos exigidos por lei, como o código "060" nos arquivos TXT.
3. **Comunicação e Cobrança:** O processo de envio de orçamentos e a gestão de assinaturas ou pagamentos recorrentes costuma ser manual, aumentando a inadimplência e o tempo de resposta ao cliente.

O ENGER surge para resolver esses problemas, oferecendo um ambiente unificado de gestão B2B.

## Objetivos

### Objetivo Geral
Desenvolver e implantar a plataforma SaaS B2B ENGER para centralizar e automatizar a gestão de obras, englobando controle financeiro, gestão de força de trabalho e conformidade fiscal tributária.

### Objetivos Específicos
* Desenvolver um construtor de orçamentos interativo, substituindo telas de visualização estática por uma interface de manipulação de dados em tempo real.
* Implementar o controle de presença de funcionários alocados por obra.
* Automatizar a geração profissional de orçamentos em PDF e seu envio via workers de background por e-mail.
* Integrar um sistema de checkout transparente e assinaturas recorrentes utilizando a API do Mercado Pago.
* Desenvolver o módulo de relatórios fiscais focados nos blocos H e K do SPED, garantindo a formatação correta de alíquotas (ex: 17.5 em vez de 17.000) e a preservação de códigos fiscais específicos.

## Stack Tecnológico

A escolha do stack tecnológico foi baseada na necessidade de escalabilidade, segurança e manutenibilidade exigidas por um sistema corporativo B2B SaaS.

* **Backend - C# (.NET Core):** Linguagem robusta e fortemente tipada, ideal para implementar as regras de negócio complexas do sistema financeiro e fiscal. Facilita a adoção de padrões arquiteturais avançados, como Domain-Driven Design (DDD) e Clean Architecture, garantindo o isolamento da lógica de domínio.
* **Frontend - React com Tailwind CSS:** O React permite a criação do construtor de orçamentos interativo de forma componentizada. O Tailwind CSS foi escolhido para agilizar a estilização da identidade visual corporativa do projeto, baseada em alto contraste com as cores laranja, preto e branco, suportando nativamente a alternância entre dark mode e light mode.
* **Banco de Dados - PostgreSQL e SQL Server:** Sistemas gerenciadores de banco de dados relacionais essenciais para manter a integridade de dados financeiros, movimentação de inventário (tabelas "Diario") e controle de acesso.
* **Infraestrutura e DevOps - Docker, Docker Compose e GitHub Actions:** O Docker garante a padronização dos ambientes de desenvolvimento e produção, orquestrando a API e os bancos de dados simultaneamente. O GitHub Actions foi adotado para a esteira de CI/CD, automatizando testes de unidade sempre que novos commits são enviados para a branch `develop`.

## Descrição da Solução

O ENGER é uma plataforma SaaS B2B desenhada para atender empresas do setor da construção civil de ponta a ponta. O sistema opera em uma arquitetura baseada em serviços e processos assíncronos. 

Na interface do usuário, destaca-se o construtor de orçamentos, uma tela altamente interativa onde os gestores podem precificar materiais e serviços com precisão, contando com um tratamento de interface limpo que exibe valores decimais formatados de forma amigável (sem zeros à direita desnecessários em alíquotas). O frontend apresenta uma identidade visual forte e corporativa nas cores laranja, preto e branco.

No backend, a solução integra-se à API do Mercado Pago para realizar a tokenização de cartões e gerenciar rotas de pré-aprovação de assinaturas recorrentes. Além disso, o sistema conta com rotinas de background (workers) dedicadas à compilação de dados de orçamento utilizando bibliotecas de PDF, enviando-os automaticamente por e-mail para os clientes finais. 

Para a área contábil, o sistema extrai dados de movimentação de inventário em tempo real para gerar os arquivos TXT do SPED fiscal (blocos H e K), aplicando regras estritas de validação de CST/CFOP para garantir a conformidade.

## Arquitetura

O ENGER adota o padrão **Domain-Driven Design (DDD)** aliado aos conceitos de **Clean Architecture**, isolando as regras de negócio da camada de infraestrutura e entrega. A autenticação é gerenciada via tokens JWT em uma camada de serviço dedicada.

Artefatos gerados para o projeto:
1. **Diagrama Entidade-Relacionamento (ER):** Modelagem das tabelas de obras, funcionários, orçamentos e tabelas "Diario" para inventário.
2. **Wireframes e Protótipos:** Design das telas nos modos claro e escuro (laranja/branco e laranja/preto), destacando o construtor interativo.
3. **Documentação de CI/CD:** Arquivos de workflow do GitHub Actions detalhando a execução de testes automatizados na branch `develop`.
4. **Casos de Uso e Histórias de Usuário:** Mapeamento das rotinas de checkout transparente e geração do SPED fiscal.
5. **Configuração de Infraestrutura:** Arquivos `Dockerfile` e `docker-compose.yml` para orquestração local.

*(Nota: Adicione aqui o link para o seu repositório no GitHub).*

## Validação

### Estratégia
A validação das regras de negócio, especialmente as regras de banco de dados e requisitos funcionais, é realizada através de homologação contínua utilizando dumps de banco de dados e especificações providenciadas pela supervisão técnica do projeto. Os fluxos de CI/CD garantem que os testes unitários sejam validados a cada integração. O construtor interativo de orçamentos e as formatações decimais foram refinados através de feedback direto e revisões de interface.

### Consolidação dos Dados Coletados
*(Nesta seção, futuramente, você deverá incluir gráficos de desempenho da API, percentual de testes passando no GitHub Actions ou feedback de usabilidade do sistema).*

## Conclusões
O desenvolvimento do ENGER demonstra a viabilidade de unificar a gestão operacional de obras com as complexidades fiscais brasileiras em uma única plataforma SaaS. A adoção de DDD e Clean Architecture permitiu criar um sistema escalável, enquanto as correções de usabilidade, como o construtor interativo e as melhorias de layout, garantiram uma ferramenta prática para o usuário final. 

**Limitações do Projeto e Perspectivas Futuras:**
*(Adicione aqui possíveis evoluções, como integração com novos gateways de pagamento, uso de IA para prever custos de obra, etc).*

## Referências Bibliográficas
*(Adicione aqui as referências técnicas de documentações usadas, como a do React, .NET Core, SPED Fiscal, Mercado Pago API, etc).*
