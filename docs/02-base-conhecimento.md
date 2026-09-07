# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

[Sua descrição aqui]

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

[Este documento apresenta a base de dados oficial e estruturada que o Agente Yosef utiliza para guiar usuários iniciantes.Para garantir a máxima segurança de um público que está começando a economizar do zero, os dados não foram extraídos de repositórios voláteis ou de renda variável. A base de conhecimento foi construída de forma estática com foco em **Ativos de Proteção e Renda Fixa com Liquidez Diária**, utilizando as diretrizes de fábrica do Tesouro Nacional e do Fundo Garantidor de Crédito (FGC).]

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

[Os dados estruturados da nossa tabela de Renda Fixa e a Regra dos 20% são injetados diretamente no **System Prompt (instruções de fábrica do agente)** como uma base estrita de contexto (técnica de Few-Shot e Context Injection). 

O agente não faz consultas dinâmicas à internet para evitar o risco de "alucinação" ou de capturar informações falsas ou desatualizadas. Toda resposta gerada deve, obrigatoriamente, cruzar a pergunta do usuário com esta base estática injetada.]

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Este é o formato real de como o sistema organiza os dados do usuário iniciante antes de enviá-los para o processamento do robô Yosef:

```text
 CONTEXTO DO USUÁRIO:
- Status: Iniciando uma economia do zero
- Renda Mensal Declarada: R\$ 3.000
- Meta Atual: Criar a Reserva de Segurança (Emergência)

 BASE DE CONHECIMENTO INJETADA:
- Regra Essencial: Guardar 20% da renda mensal (R\$ 600 neste caso) na entrada do salário.
- Produto Recomendado 1: Tesouro Selic (Liquidez Diária, Segurança do Estado).
- Produto Recomendado 2: CDB 100% do CDI (Liquidez Imediata, Proteção do FGC).

 DIRETRIZ DE SEGURANÇA:
- Proibido sugerir qualquer ativo de risco ou renda variável.
- Se o usuário perguntar sobre "Ações" ou "Cripto", responder que não possui esses dados.
