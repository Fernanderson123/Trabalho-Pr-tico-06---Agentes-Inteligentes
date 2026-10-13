1. Escolha do domínio
O enunciado do Trabalho Prático 06 de Inteligência Artificial (GCC128) pede uma aplicação simples, com pelo menos dois agentes inteligentes, uma ferramenta definida com @tool, um LLM gratuito e um framework como LangGraph.
Minha sugestão é desenvolver um Assistente de Avaliação de Acessibilidade de Interfaces Web.
A proposta aproveita conceitos de UX/UI e IHC que você já conhece, sem exigir um sistema complexo, banco de dados ou interface gráfica.
Como funcionaria?
Imagine que você está avaliando o contraste entre o texto de um botão e seu fundo.
Exemplo de entrada
<img width="717" height="247" alt="image" src="https://github.com/user-attachments/assets/946b85c8-b737-424c-8bb9-7e240e355e4c" />
Continuar

Texto: #FFFFFF · Fundo: #777777

Contraste calculado
4,48:1

Não atende AA
Texto normal (mínimo 4,5:1)


A aplicação receberia as duas cores e produziria uma avaliação explicando se o contraste atende aos critérios WCAG, além de sugerir melhorias.
2. Escolha dos dois agentes
Entrada do usuário
Cores do texto e do fundo

Agente 1 — Auditor de Acessibilidade
Utiliza @tool para calcular o contraste e interpreta o resultado

Agente 2 — Consultor UX
Analisa o diagnóstico, explica o impacto e recomenda melhorias

Relatório final


Essa divisão demonstra colaboração real: o primeiro agente fornece uma avaliação técnica fundamentada em um cálculo, enquanto o segundo transforma o diagnóstico em recomendações práticas.
Por que essa escolha é interessante para a nota? Você conseguirá demonstrar separadamente a função de cada agente, a ferramenta, a comunicação entre eles e a resposta final. Tudo isso em um notebook relativamente pequeno.
Vou usar Python + LangGraph + Groq, seguindo as opções do enunciado, e deixar o código organizado em células para facilitar sua compreensão.
3. Notebook inicial criado
O arquivo contém os imports, a ferramenta @tool, a implementação dos dois agentes, o grafo de execução, um exemplo prático e testes básicos.
Validei a sintaxe das células Python, mas a execução completa com Groq ainda precisa ser testada, pois depende de sua chave de API e do acesso ao modelo.
Como começar
1. Abra o notebook no VS Code ou Google Colab.
2. Execute a instalação das bibliotecas.
3. Configure a chave gratuita obtida em Groq Console.
4. Execute as células na ordem apresentada.
5. Observe a saída da ferramenta, o diagnóstico do auditor e as recomendações do consultor.
A estrutura do grafo segue a API documentada do LangGraph. 

GitHub
+1



4. O que você precisa entender antes de avançar
Para compreender o projeto e conseguir explicá-lo ao professor, eu focaria inicialmente em três elementos: a ferramenta, que executa o cálculo; os agentes, que utilizam um modelo de linguagem para interpretar e recomendar; e o grafo, que determina a ordem de execução e transmite as informações.
Uma observação importante: nesta versão, o Auditor chama a ferramenta diretamente por código, de forma obrigatória. Isso simplifica a aplicação e garante que o contraste sempre seja calculado. Posteriormente, podemos experimentar uma versão na qual o próprio LLM decide quando chamar a ferramenta.
Minha sugestão é começar executando e entendendo até a célula da ferramenta @tool, antes de avançarmos para os agentes. Assim você consegue dominar a lógica do programa, em vez de apenas executar um notebook pronto.
