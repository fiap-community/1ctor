# README.md  

### Equipe:

- **Adriano Aguiar Alves:** RM360803@fiap.com.br

- **Christiano Augusto Araújo Ferreira:** RM362243@fiap.com.br

- **Marina Pena Cavalieri:** RM360357@fiap.com.br

- **Roger Abia Souza:** RM362397@fiap.com.br

## Etapas e Arquitetura  

### 1. Configuração do Ambiente  
Preparação e configuração do ambiente de desenvolvimento, garantindo que todas as ferramentas e plataformas necessárias, como o Databricks para processamento de dados e o GitHub para controle de versão, estejam devidamente configuradas e integradas de acordo com as necessidades do pipeline de dados.

---

### 2. Web Scraping e Coleta de Dados  
Implementação de um processo automatizado de web scraping para coletar conjuntos de dados de fontes públicas, garantindo que os dados mais recentes disponíveis sejam sempre obtidos sem intervenção manual.  

Principais aspectos incluem:  

- **Automação:** Elimina downloads manuais repetitivos, reduzindo erros humanos.  
- **Atualização dos Dados:** Sempre obtém a versão mais recente de cada conjunto de dados para análise.  
- **Escalabilidade:** Facilmente extensível para múltiplos portais de dados ou conjuntos de dados adicionais.  
- **Reprodutibilidade:** Garante um processo consistente para obtenção de dados brutos, essencial para auditorias e conformidade.  

---

### 3. Armazenamento de Dados no Unity Catalog  
Os dados brutos obtidos por meio de scraping são salvos como arquivos de origem no **Unity Catalog**, e as futuras camadas da arquitetura Medallion são salvas como tabelas Delta, com os seguintes objetivos:  

- Armazenamento centralizado com controle de acesso seguro.  
- Integração com o Databricks para acesso automatizado aos dados.  
- Suporte à governança e rastreabilidade dos dados.  

**URL da fonte de dados:**  

https://dados.gov.br/dados/conjuntos-dados/grandes-nmeros-do-imposto-de-renda-da-pessoa-fsica  

---

### 4. Arquitetura Medallion  
Implementação da arquitetura Medallion no Databricks para garantir:  

- **Bronze:** ingestão de dados brutos.  
- **Silver:** limpeza, padronização e enriquecimento.  
- **Gold:** dados prontos para análise e modelagem.  
- Alta escalabilidade, fácil manutenção e retenção de dados históricos.  

---

### 5. Modelagem em Tabelas Wide  
Modelagem voltada para análises rápidas e flexíveis:  

- Todos os dados em uma única tabela.  
- Esquema desnormalizado com dados previamente integrados (joins realizados).  
- Otimizado para exploração rápida de dados e machine learning.  

---

### 6. Ingestão de Dados com Databricks Workflows  
Uso do **Databricks Job Workflows** para ingestão e transformação de dados:  

- Pipeline orquestrado para transformar dados brutos em dados estruturados.  
- Execução agendada.  
- Compatível com a arquitetura Medallion (bronze, silver, gold).  

---

### 7. Documentação no Unity Catalog  
Uso de descrições e tags para:  

- Facilitar o entendimento e uso das tabelas.  
- Habilitar a funcionalidade do Genie com metadados contextuais.  
- Melhorar a governança e acessibilidade dos dados.  

---

### 8. Genie (Assistente de Dados)  
Ferramenta integrada ao Databricks que permite:  

- Execução de consultas comuns por meio de linguagem natural.  
- Suporte a perguntas frequentes sobre os dados (FAQ).  
- Interface amigável para usuários de negócio e analistas.  