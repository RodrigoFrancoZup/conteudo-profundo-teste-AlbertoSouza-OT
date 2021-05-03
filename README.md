# conteudo-profundo-teste-AlbertoSouza-OT
Repositório destinado ao Resumo do Curso: Conteúdo mais profundo sobre testes (Técnicas de Teste) - Alberto Souza

Nesse curso aprendemos:

⦁	A diferença de perspectiva da academia e do mercado sobre os testes. A Academia usa o teste para descobrir erros, bugs. Já o mercado usa para garantir que uma refatoração ou implementação de novas funcionalidades não tenha danificado algo (erros de propagação). Devemos juntar essas duas perspectivas;

⦁	Vamos buscar a revelação de bugs antes que chega em produção (ao cliente);

⦁	Conjunto de técnicas de teste é mais importante que a quantidade de linhas testadas (cobertura de testes em 90%, baseada em linhas de código);

⦁	Literatura sugere fortemente o TDD, embora a justificativa do TDD faça sentido, ainda não há comprovação científica. Para o Alberto (mentor) o importante é testar. TDD é melhor que não fazer teste, o TDD também ajuda você programar, mas se você não optar por TDD, mas depois de codificar e testar, então está tudo bem. Muitas indústrias adotaram o TDD;

⦁	Vamos focar em testes de unidade, mas o ideal é a combinação dos testes de unidade, com teste de integração, com testes de sistema, e com testes manuais. Essa é a pirâmide de testes (base é teste de unidade);

⦁	Técnica specification based test: Pensar em cenário de teste através das especificações (tarefas a fazer - cartões de tarefas - quadro de tarefas - Trello...). Podemos consultar o livro do Maurício Aniche e ver o roteiro que devemos seguir para analisar a atividade a ser desenvolvida e extrair dela os cenários de teste;

⦁	Não precisamos testar todas as combinações possíveis, e sim os cenários possíveis (lembre-se do exemplo de Tipos de pagamento que restaurante aceita x Tipos de pagamentos que o usuário aceita - no qual o importante é testar quando restaurante e usuário aceitam os mesmos métodos de pagamento (combinam em 100%), quando os dois não combinam (cada um tem uma forma diferente) e quando combinam parcialmente (cliente tem apenas uma forma igual o restaurante);

⦁	Testar todas as combinações pode nos levar a cair no erro de estar testando as Classes de Equivalência;

⦁	Técnica boundary test: Dado que eu tenho uma condicional (IF) devo criar cenário caindo na condição e para não cair na condição, mas tem que ficar claro os valores e os limites que vão levar a gente cair e não cair no IF. Essa técnica sugere usar o valor máximo para cair e um para não cair na condição, por exemplo se em um IF a nota tem que ser > 6 para entrar no if, devemos escolher o teste com 7, outro teste com  6, um teste com  valor maior tipo 10 que faz cair no IF e um com valor muito longe do ponto que não cai no if como nota com valor 1;

⦁	Técnica structural testing: é a técnica mais utilizada, pensamos em cobertura do código, olhamos o código primeiro para levantar os cenários. Definimos também o quanto vamos cobrir, 70%, 80% ou 90%. Essa porcentagem pode ser sobre quantidade de linhas, quantidade de branchs, quantidade de condicionais. Aqui a equipe pode definir como vai testar as condições, com quais valores, como vai testar os loopings...;

⦁	Condicional mencionado anteriormente é o valor dos atributos que te faz cair no IF, branch é entrar no trecho do if{} e do else{}, por exemplo: em uma condicional OR true / false, false e true não testa todas as branchs, pois não entra nunca no else. Devemos testar as condicionais e as branchs;

⦁	Path coverage MCDC: é uma tática da técnica structural testing, que aplicamos em condicionais que resulta em N+1, onde N é o número de condições, ou seja, se temos 5 condições devemos no mínimo fazer 6 combinações de teste. 
	Exemplo de condições: if(nota > 7 || aluno.fezMetoria == true){}. Aqui temos duas condições, devemos fazer no mínimo 3 testes com os bons pares.
	Sem essa técnica teríamos que aplicar a regra X^Y, onde X é o tipo de valor que a condição pode ter e Y é a quantidade de parâmetros de condições, no exemplo acima teríamos 2^2 = 4 condições, o primeiro  2 (X) é pelo fato das condições poderem ser falsa ou verdadeira e o segundo 2 é o Y, pois temos 2 condições.
	Com essa técnica reduzimos o número de combinações que devemos testar.
	Essa tática é feito com a "troca" de valores utilizando a Tabela Verdade, vamos fazer a "troca" sempre analisando uma única coluna, e depois de analisar todas colunas vamos selecionar os bons pares;

⦁	Técnica Self Testing: essa visa fazer o seu próprio código se testar, sem que criemos testes automatizados. Ela se mistura com a técnica de desenvolvimento de software Design by Contract. Devemos estabelecer condições, que se não respeitadas devemos parar o fluxo de execução, na prática seria se um método de nossa aplicação não segue o contrato, então devemos parar o mesmo para refatorá-lo. Para forçar essa parada, podemos lançar uma Exception com Assert(Condição que se acontecer vai lançar Excepetion).
	Outro maneira que podemos aplicar essa técnica é pegar um objeto que não pode ter atributos nulos (tanto que seu construtor já tem 	parâmetros) e em todos os métodos que esse objeto passe nós devemos verificar se em nenhum momento o atributo ficou nulo. 	Exemplo: Objeto Aluno já é criado com matrícula, ao ele passar no método verificaSeAlunoPassou(Aluno aluno) eu devo verificar se ele não ficou com atributo matricula como nulo;

⦁	Nesta Jornada (Oragen Talents) vamos focar em Testes de Unidade, em Orientação de Objetos vamos pensar em testar o método de uma classe. O perigo desse teste é testá-lo fora do contexto do software (ficar criando muito mocks) e isso não apontar o bug. Depois vamos para os testes de integração, no caso testar os métodos que vão executar as Querys (conversam com banco de dados). Por fim o teste de sistema, por exemplo, em uma API o teste de sistema se resume em subir a API e ver se ela subiu;

⦁	O teste quanto mais integrado, indica que mais perto da realidade estamos (quanto mais próximo do topo da Pirâmide do Teste mais próximo da realidade). Por exemplo: criar um teste criando objetos do framework Spring. O problema ocorre se na próxima versão a classe do Spring mudar, certamente o teste quebra, mas vai nos apontar que esse foi o "bug";

⦁	Mocks: Devemos dar preferência para fazer os testes de unidade com a integração, mas essa integração deve ser com as classes criadas por nós, que podemos dar new() facilmente e que estão rodando na memória. Agora, quando precisamos de serviços externos, com classes por exemplo do framework, podemos utilizar o Mockito para criar nossos mocks. Mocks é a simulação de um serviço externo, no qual podemos escolher qual resposta teremos (o serviço que ocorre não é o original);

⦁	Resumo das Técnicas que vamos combinar nessa jornada (Orange Talents): Para cada funcionalidade (requisitos funcoinais) que temos, devemos focar primeiramente no desenvolvimento seguindo um bom designer, para depois testá-lo (não vamos utilizar o TDD). Esses testes devem utilizar as técnicas: boundary test, structural testing (com MC/DC) e Self Testing. Vamos aplicar testes de unidade apenas onde há condicional e branch, e condicionais e branchs escritos por nós. (A Literatura pede-se para testar tudo, mas não vamos seguir esse caminho);

⦁	Em qualquer linguagem devemos escolher uma Biblioteca de Testes e uma ferramenta de Mocks e ser bom nelas!
