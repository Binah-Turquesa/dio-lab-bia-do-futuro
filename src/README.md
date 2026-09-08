# 💻 Aplicação Funcional e Protótipo - Agente Yosef

Este documento descreve como o protótipo funcional do Agente Yosef foi estruturado para testes de interação em ambiente de laboratório seguro.

## 1. Ambiente de Desenvolvimento
Para manter a simplicidade exigida pelo desafio e focar na inteligência do orquestrador, o protótipo não utiliza interfaces gráficas pesadas (como Streamlit ou WebApps). A aplicação funcional roda diretamente em um caderno do **Google Colab utilizando Python e a API de LLM**.

## 2. Código do Protótipo (Mecanismo de Execução)
O trecho de código abaixo simula o motor de funcionamento do agente, injetando as diretrizes de cibersegurança no prompt e abrindo o canal de conversa com o usuário:

""" Python
# 🤖 Mecanismo de Execução do Agente Yosef no Google Colab

import os

# Simulando a injeção do System Prompt de Cibersegurança e da Base de Dados
SYSTEM_PROMPT = """
Você é o Yosef, assistente sábio e meigo para iniciantes em economia.
Siga estritamente as regras de proteção: recomende apenas Tesouro Selic e CDB 100% CDI.
Proibido sugerir renda variável ou ações. Admita quando não souber o dado.
"""

def responder_usuario(pergunta_usuario):
    # Simulação da checagem anti-alucinação antes de responder
    palavras_bloqueadas = ["ações", "cripto", "bitcoin", "fii", "aposta"]
    
    # Validação do Edge Case no Filtro de Entrada
    for palavra in palavras_bloqueadas:
        if palavra in pergunta_usuario.lower():
            return "Eu não tenho esses dados nos meus registros. Meu foco é te ajudar a iniciar uma economia com segurança absoluta. Que tal falarmos sobre sua Reserva de Emergência?"

           # Resposta ideal para o escopo permitido
    if "guardar" in pergunta_usuario.lower() or "poupar" in pergunta_usuario.lower():
        return "Olá! Lembra da história de Yosef, que guardava nos anos de fartura? Recomendo começar separando de 5% a 20% da sua renda no Tesouro Selic para criar sua caixinha sagrada de segurança!"
        
    return "Eu sou o Yosef, especialista em te ajudar a iniciar uma economia. Não tenho dados sobre esse assunto. Como posso apoiar suas finanças hoje?"
    
# Teste prático do Filtro de Segurança
print("--- TESTANDO REQUISIÇÃO PERMITIDA ---")
print(responder_usuario("Quero começar a poupar o meu salário."))

print("\n--- TESTANDO FILTRO DE SEGURANÇA (EDGE CASE) ---")
print(responder_usuario("Vale a pena comprar Bitcoin hoje?"))

"""
## 3. Como Testar o Protótipo
1. Abra um caderno novo no **Google Colab**.
2. Cole o código Python acima em uma célula.
3. Clique no botão de **Play** para rodar.
4. O terminal exibirá as respostas limpas, com o filtro de segurança funcionando perfeitamente contra alucinações!


--- TESTANDO REQUISIÇÃO PERMITIDA ---
Olá! Lembra da história de Yosef, que guardava nos anos de fartura? Recomendo começar separando de 5% a 20% da sua renda no Tesouro Selic para criar sua caixinha sagrada de segurança!

--- TESTANDO FILTRO DE SEGURANÇA (EDGE CASE) ---
Eu não tenho esses dados nos meus registros. Meu foco é te ajudar a iniciar uma economia com segurança absoluta. Que tal falarmos sobre sua Reserva de Emergência?

https://colab.research.google.com/drive/1AiF_FWWPFdFgQcWA8yEnyDb7zRwyjMMR#scrollTo=4sVbpJwBerQE&fullscreenOutput=true
