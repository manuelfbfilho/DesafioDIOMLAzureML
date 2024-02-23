<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="40px" src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png"></a>
    <span> Desafio Machine Learning na Prática no Azure ML</span>
</h1>

Repositório criado como atividade para avaliação parcial do treinamento para realizar a prova de certificação no Microsoft Azure AI Fundamentals (AI Fundamentals +AI-900) da [Digital Innovation One](https://www.dio.me/).


## Objetivo 🎯
Conhecer o Azure e aprender a utilizar a plataforma e unir o conhecimento teórico com a prática.


## Passo-a-Passo 🛠️

### 1. Crie um novo repositório no GitHub
   * 1.1 Vá para o GitHub e faça login na sua conta.
   * 1.2 Clique em + no canto superior direito e selecione New repository.
   * 1.3 Dê um nome ao seu repositório e clique em Create repository.


### 2. Criar um espaço de trabalho (workspace) do Azure Machine Learning
Para utilizar o Azure Machine Learning, é necessário aprovisionar um espaço de trabalho do Azure Machine Learning na sua subscrição do Azure. Depois, você poderá usar o estúdio Azure Machine Learning para trabalhar com os recursos do seu workspace.<br><br>
<b>Ps:</b> Se você já tiver um espaço de trabalho do Azure Machine Learning, poderá usá-lo e pular para a próxima tarefa.<br><br>

2.1 Entre no portal do Azure em https://portal.azure.com usando suas credenciais da Microsoft.<br>
2.2	Selecione + Criar um recurso , pesquise Machine Learning e crie um novo recurso do Azure Machine Learning com as seguintes configurações:<br>
&nbsp;&nbsp;&nbsp;2.2.1	Assinatura : sua assinatura do Azure.<br>
&nbsp;&nbsp;&nbsp;2.2.2	Grupo de recursos : Crie ou selecione um grupo de recursos.<br>
&nbsp;&nbsp;&nbsp;2.2.3	Nome : Insira um nome exclusivo para seu espaço de trabalho.<br>
&nbsp;&nbsp;&nbsp;2.2.4	Região : Selecione a região geográfica mais próxima.<br>
&nbsp;&nbsp;&nbsp;2.2.5	Conta de armazenamento : observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho.<br>
&nbsp;&nbsp;&nbsp;2.2.6	Cofre de chaves : Observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho.<br>
&nbsp;&nbsp;&nbsp;2.2.7	Insights de aplicativo : observe o novo recurso padrão de insights de aplicativo que será criado para seu espaço de trabalho.<br>
&nbsp;&nbsp;&nbsp;2.2.8	Registro de contêiner : Nenhum ( um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).<br>
2.3	Selecione Revisar + criar e selecione Criar . Aguarde a criação do seu espaço de trabalho (pode demorar alguns minutos) e, em seguida, vá para o recurso implantado.<br>
2.4	Selecione Launch Studio (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no Azure Machine Learning Studio usando sua conta da Microsoft). Feche qualquer mensagens que são exibido.<br>
2.5	No estúdio Azure Machine Learning, você deverá ver seu espaço de trabalho recém-criado. Caso contrário, selecione Todos os espaços de trabalho no menu à esquerda e selecione o espaço de trabalho que você acabou de criar.<br><br>

### 3. Use aprendizado de máquina automatizado para treinar um modelo
<I>“O aprendizado de máquina automatizado permite que você experimente vários algoritmos e parâmetros para treinar vários modelos e identificar o melhor para seus dados. Neste exercício, você usará um conjunto de dados de detalhes históricos de aluguel de bicicletas para treinar um modelo que prevê o número de aluguel de bicicletas esperado em um determinado dia, com base em características sazonais e meteorológicas.”</I><br>
<b>> Citação:</b> Os dados usados neste exercício são derivados da Capital Bikeshare e são usados de acordo com o contrato de licença de dados publicado.<br><br>
3.1	No Azure Machine Learning Studio , veja a página Automated ML (em Authoring).<br>
3.2	Crie um novo trabalho de ML automatizado com as seguintes configurações, usando Next conforme necessário para avançar pela interface do usuário:<br>
&nbsp;&nbsp;&nbsp;<b>> Configurações básicas:</b><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Trabalho nome : mslearn - bicicleta - automl<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Nome do novo experimento : mslearn -bike-rental<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Marcadores : nenhum<br>

&nbsp;&nbsp;&nbsp;<b>> Tipo de tarefa e dados:</b><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Selecione tarefa tipo : Regressão<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Tipo de dados:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Nome: bicicleta - aluguel<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Descrição: Histórico bicicleta dados de aluguel<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tipo: Tabular<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Fonte de dados:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Selecione <b>De arquivos da web</b><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* URL da Web:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;URL da Web: https://aka.ms/bike-rentals<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ignorar validação de dados: não selecionar<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Configurações:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Formato de arquivo: Delimitado<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Delimitador: Vírgula<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Codificação: UTF-8<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Cabeçalhos de coluna: apenas o primeiro arquivo possui cabeçalhos<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Pular linhas: Nenhuma<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O conjunto de dados contém dados multilinhas: não selecione<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Esquema:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Incluir todas as colunas exceto Caminho<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Reveja o automaticamente detectou tipos<br><br>
* Selecione Criar . Após a criação do conjunto de dados, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.<br><br>
&nbsp;&nbsp;&nbsp;<b>> Configurações de tarefa:</b><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Tipo de tarefa: Regressão<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Conjunto de dados: bicicleta - aluguel<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Coluna de destino: Aluguéis (inteiro)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Adicional definições de configuração:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Métrica primária: raiz do erro quadrático médio normalizado<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Explicar melhor modelo: Não selecionado<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Usar todos os modelos suportados : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modelos permitidos: Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Limites: Expandir esse seção<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Máximo de testes: 3<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Máximo simultâneo testes: 3<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Máximo de nós: 3<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Limite de pontuação da métrica : 0,085 (para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tempo limite: 15<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tempo limite de iteração: 15<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Habilitar cedo rescisão: selecionado<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Validação e teste:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Validação tipo: divisão de validação de trem<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Percentagem de dados de validação: 10<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Conjunto de dados de teste: Nenhum<br>
&nbsp;&nbsp;&nbsp;<b>> Calcular:</b><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Selecione o tipo de computação: sem servidor<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Tipo de máquina virtual: CPU<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Camada de máquina virtual: Dedicada<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Tamanho da máquina virtual: Standard_DS3_V2*<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* Número de instâncias: 1<br><br>
* Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.<br><br>
4.	Envie o trabalho de treinamento. Ele inicia automaticamente.
* Espere o trabalho terminar. Pode demorar um pouco! (Em geral essa execução dura em torno de 15 muntos)
5. Após finalizado, no menu lateral esquerdo iremos clicar em <i>Modelos</i>.
6. Clicaremos em <i>+Registro</i> e selecionaremos a opção <i>'de uma saída de trabalho'</i>.
7. Selecionaremos o trabalho que criamos que é o <i>'mslearn-bike-automl'</i> e clicaremos em avançar.
8. Na parte de selecionar saída, já irá aparecer preenchido como padrão, deixe como estiver.
  * Tipo de Modelo: MLflow Saída de trabalho: best_model...
9. Em configuração do modelo, coloque as informações abaixo e clique em avançar.
  * Nome: mslearnbikeauto4
  * Descrição: Deixe em branco.
  * Versão: 1
  * Marcas: Não precisa adicionar
10. Em examinar, clique em <i>registro</i>.
11. No menu lateral esquerdo, agora clicaremos em <i>Pontos Extremidade</i>.
12. Em pontos de Extremidade clicaremos e Criar e então selecionaremos 'mslearnbikeauto4', e clicaremos no botão selecionar.
13. Na aba de implantar, altere o nome do ponto de extremidade para 'laboratoriocertificaoai900-extr' e clique em implantar e espere a conclusão do processo.
14. Após a conclusão da criação do ponto de extremidade, você deverá clica no menu lateral em ponto de extremidade, selecionar então o ponto de extremidade criado e clicar em testar.
15. Na aba 'inserir dados para teste de ponto de extremidade', insira os seguintes dados em JSON e clique em testar.<br>
\```json
{
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
}
\```


16. O Resultado será apresentado no quadro resultado do teste. Copie o resultado e cole em um bloco de notas com nome <i>ResultadoPredict-Rentals.json</i>

#### Parabéns! Você fez todo o processo!

---
##  Desafio: Profile README

### Como Entregar esse projeto?
Chegou a hora de você construir um portfólio ainda mais rico e impressionar futuros recrutadores, para isso é sempre importante mostrar os resultados do seu esforço e como você os obteve deixando claro o seu racional, para isso faça da seguinte maneira: 😊💙.

1. Crie um novo repositório no github com um nome a sua preferência
2. Crie um modelo de previsão com seus devidos pontos de extremidade configurados
3. Escreva o passo a passo desse processo em um readme.md de como você chegou nessa etapa
4. Salve nesse repositório o readme.md e o arquivo .json de pontos de extremidade
5. Compartilhe conosco o link desse repositório através do botão 'entregar projeto'

---

## Contatos 
[![Linkedin](https://img.shields.io/badge/Linkedin-000?style=for-the-badge&logo=linkedin&logoColor=30A3DC)](https://www.linkedin.com/in/manuelfbfilho)
<br>
[![GitHub](https://img.shields.io/badge/GitHub-000?style=for-the-badge&logo=github&logoColor=30A3DC)](https://github.com/manuelfbfilho)
