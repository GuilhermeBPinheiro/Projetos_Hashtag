# Projetos_Hashtag

Esse repositório foi criado com base em documentar e colocar projetos realizados durante 
imersões em: Ciências de Dados, Python, JavaScript, Excel, PowerBI, com diferentes aplicações.
Os intensivões ou jornadas, acontecem geralmente durante algumas semanas do ano. 

Fonte: [Hashtag Treinamentos](https://www.hashtagtreinamentos.com/cursos-hashtag-programacao?origemurl=136986055125&gad=1&gclid=CjwKCAjws9ipBhB1EiwAccEi1AwnRJAKkGpnBqFHQgcwKSLCRy1DUVtYPaLLOviFEX_Fz3HQaLFl7xoCP6wQAvD_BwE).
_______________________________________________________________________________

## Intensivão em Python 

### Aula 1 | Python Power Up
* Projeto: Automação de um Sistema para Preenchimento de Formulário 

* ### Parte 1 | Introdução

Nessa aula **Python Power Up**, iremos criar um projeto de automação com intuito de acelerar a automação de tarefas. Imagine que trabalhe num sistema e-commerce e necessite preenche um planilha de cadastro que contém: produtos, preços e outras informações adicionais. Quanto maior quantidade de informações que precisa ser preenchido, mais trabalhoso vai ser, e fazer isso manual é seria muito cansativo. Então, a linguagem Python vai permitir automatizar esse processo, e vai fornecer o controle via mouse e teclado. 

Descrição do Projeto:
> Consiga entrar num site, realizar seu login e fazer o cadastro de todos os produtos de forma automática.

Material do Projeto:
> Era fornecido uma base de dados e um site próprio para conseguir extrair as informações. Porém, para tentar criar um projeto autoral, os dados foram auterados. As informações estão dentro de um arquivo de extensão CSV (produtos.csv). Fonte: Kaggle.

 ### **Projeto:**

Contextualização:
> O  código do produto, marca, tipo, preço unitário, custo e observação. Só que o primeiro ponto, é que as informações estão no formato csv, o que dificulta um pouco a visualização.
Outro pronto é que termos 300 linhas de informação, então você teria que preencher 6 informações no sistema para cada linha de base de dados.

Solução:
> Vai ser exatamente a nossa automação, ou seja, ter no final todos os produtos da nossa base de dados cadastrados no sistema de forma automática, como se estivesse utilizando a máquina para realizar o cadastro. Ao rodar o algoritmo ou programa, queremos que ele realiza algumas funções: abrir o navegador --> acessar o site do sistema com login e senha --> insetir todas as informações do produto --> enviar as informações para o sistema --> repetir o cadastro até acabar o cadastro de todos os produtos.

Observação:
> Todo crédito se dá para a equipe técnica do **Hash Treinamento**. Existem outros modelos de automatação, no qual pegar informações de uma página e criar um arquivo CSV, no qual dá para integrar junto a esse. Basicamente, criar um algoritmo para pegar informações e outro para cadastrar essas informações. Todavia, essa é uma versão inicial de estudo.
Ferramentas do Projeto

Sistema de Aplicação:
> Irei rodar meu código pelo sistema Visual Studio Code (VS Code) - versão 1.83. É possível fazer rodando em qualquer IDLE ou com seu próprio terminal. Porém, não recomendo usar ambiente virtuais como Google Colab ou Jupiter Notebook,  pois não possuem uma interface gráfica de usuário interativa como um sistema operacional de desktop. Portanto, algumas bibliotecas de automação de GUI, como o pyautogui, podem não funcionar diretamente nesses ambientes. Para ter acesso ao meu código, utilizarei o Google Colab para documentar, porém é necessário transpor os códigos para sua IDLE --> [códigos](https://colab.research.google.com/drive/1fPwfovnk1MFOgw2JsSffXy1y_ZBTvf4k#scrollTo=I3g9r4f2EHyg).

Ferramentas: 
> Framework PyautoGui: é necessário realizar a importação dessa biblitoeca que permitirá que voc~e controle o mouse e seu teclado para fazer as automações na máquina utilizando o Python. Para realizar a instação basta escrever pip install pyautogui no seu terminal. [Documentação](https://pyautogui.readthedocs.io/en/latest/).
>> Comandos PyautoGui:
>> * ```.press``` --> serve para pressionar uma tecla do seu teclado; 
>> * ```.write``` --> serve para escrever com o teclado (como se fosse você digitando);
>> * ```.click``` --> serve para clicar com o mouse. Em relação a esse comando, vai notar que precisamos de um posição x e y, para que ele sabia onde tem que ser clicado. Essa posição vai ser passada em relação ao SEU monitor, pois ele leva em consideração o tamanho do monitor também.

Arquivos:
> * *produtos.csv* - onde vai ter todas informações do produto;
> * *pegar_posição.py* - que tem um código para pegar a posição do seu mouse. Obs.: ao executar o código ele demora uns 5 segundos para pegar a posição, para que consiga ter tempo necessário para colocar o mouse onde precisar.

Etapas:
I.I. Abrindo o Navegador:
```
pyautogui.PAUSE = 0.5 #Define o tempo de espera entre os comandos do PyautoGui

#Abri sistema via Google Chrome.
pyautogui.press("win")
pyautogui.write("chrome") #Caso utilizei outro navegador, alterar nessa secção.
pyautogui.press("enter")
pyautogui.write("https://dlp.hashtagtreinamentos.com/python/intensivao/login") #Caso tenha seu próprio site, utilizar.
pyautogui.press("enter")

time.sleep(5) #Espera carregar
```
Obs.: Lembrar de deixar inativo a função "x" exibir na inicialização. Pois, acabaria travando na tela de selecionar o login. Uma possibilidade e até pensando em otimizar do código para possivéis erros, seria fazer entrar numa aba anônima e a partir dela acessar o link.
![image](https://github.com/GuilhermeBPinheiro/Projetos_Hashtag/assets/57289531/30c5ff5e-c138-44ca-bc3b-9894a041b975)
![image](https://github.com/GuilhermeBPinheiro/Projetos_Hashtag/assets/57289531/9a3acecd-5a4c-40b4-84a6-7fbd89368a88)

I.II. Abrindo o Navegador Anônimo:
```
# Abrir o sistema via Google Chrome em modo anônimo
pyautogui.press("win")
pyautogui.write("chrome --incognito")  # Adicione a opção --incognito para abrir em modo anônimo
pyautogui.press("enter")

# Aguarde um momento para o Chrome iniciar
time.sleep(2)

# Determinar a resolução do monitor primário
primary_screen_width, primary_screen_height = pyautogui.size()

# Calcular as coordenadas do clique com base na resolução do monitor primário
x_coordinate = primary_screen_width // 2  # Exemplo: clique no meio da largura do monitor primário
y_coordinate = primary_screen_height // 2  # Exemplo: clique no meio da altura do monitor primário

# Realize o clique
pyautogui.click(x_coordinate, y_coordinate)

# Aguarde um momento para o modo anônimo abrir completamente
time.sleep(2)

# Escreva a URL na barra de endereços e pressione Enter
pyautogui.write("https://dlp.hashtagtreinamentos.com/python/intensivao/login")
pyautogui.press("enter")

# Espere o site carregar
time.sleep(5)
```

II. Fazendo o Login:
```
#Fazer login (aqui pode preencher com qualquer dado de login)
pyautogui.click(x=1686, y=591)
pyautogui.write("pythonimpressionador@gmail.com")
pyautogui.press("tab")
pyautogui.writr("sua senha")
pyautogui.click(x=1902, y=838)
```
