# AUTOMATIZANDO-TAREFAS-COM-PYTHON---ENVIO-DE-E-MAIL-AUTOMATICO
Projeto direcionado a automatização de tarefas com o intuito de enviar e-mails automaticamente ao gestor pré-definido com analises sobre cotações de ações na bolsa.


# AUTOMATIZAÇÃO DE TAREFAS DE TRABALHO - PROJETO 02
#### Automatizando tarefas com as bibliotecas `yfinance` e `pyautogui`
##### Obs, sempre que for utilizar uma biblioteca, adicione o comando `import` antes do nome da biblioteca
Exemplos:

- `import yfinance`
- `import pyautogui`
# Passo a passo do problema que temos que resolver

- Buscar as informações da ação automaticamente
- Criar as análises solicitadas
    - Cotação máxima
    - Cotação mínima
    - Valor médio
- Enviar e-mail automaticamente para o gestor

#### Buscar dados da ação automaticamente

Bibliotecas: `yfinance` e `matplotlib`

`pip install yfinance`
`pip install matplotlib`
# Importar a yfinance
!pip install yfinance

import yfinance
# Esse código realiza a busca de datas formatadas, para preencher, o código abaixo leva em consideração uma data fechada

from datetime import datetime

data_inicio = input("Digite uma data no formato dd/mm/yyyy: ")
formato_data = "%d/%m/%Y"
periodo_inicial = datetime.strptime(data_inicio, formato_data)

data_fim = input("Digite uma data no formato dd/mm/yyyy: ")
formato_data = "%d/%m/%Y"
periodo_final = datetime.strptime(data_fim, formato_data)


ticker = input("Digite o código da ação: ")


dados= yfinance.Ticker(ticker).history(start= periodo_inicial, end= periodo_final)
fechamento = dados.Close
fechamento.plot()



ticker = input("Digite o código da ação: ")


dados= yfinance.Ticker(ticker).history(start= "2020-01-01", end= "2020-12-31")
fechamento = dados.Close
grafico = fechamento.plot()





#### Criar as analises solicitadas

- Cotação máxima
- Cotação minima
- Valor médio

##### round (Valor que deseja arredondadar, quantidade de casas) - Esse comando realiza o arredondamento dos valores
maxima = round(fechamento.max(),2)
minima = round(fechamento.min(),2)
valor_medio = round(fechamento.mean(),2)



print(maxima)
print(minima)
print(valor_medio)




#### Enviar e-mail com as analises

- Abrir o navegador e ir para o Gmail
- Clicar no botão escrever
- Digitar o e-mail do destinatário e Teclar TAB
- Digitar o assunto do e-mail e Teclar TAB
- Digitar a mensagem 
- Clicar no botão ENVIAR

biblioteca: pyautogui e piperclip, webbrowser

`pip install pyautogui` `pip install piperclip` `pip install webbrowser`
#### Bibliotecas
import pyautogui
import pyperclip
import webbrowser
import time 

destinatario = "lucassaguilar500@gmail.com"
assunto = "Analises do projeto 02"

mensagem = f""""

Prezado gestor,


Seguem as analises solicitadas da ação {ticker}:

Cotação máxima: R$ {maxima}
Cotação minima: R$ {minima}
Valor médio:    R$ {valor_medio}


Qualquer duvida estou á disposição!


Atte.

"""

#Abrir o navegador  e ir para o Gmail

webbrowser.open("www.gmail.com")
time.sleep(3)

#Configurando uma pausa de 3 segundos
pyautogui.PAUSE = 3

pyautogui.click(2089,198)

# Copiar o e-mail do destinatário

pyperclip.copy(destinatario)
pyautogui.hotkey("CTRL","v")
pyautogui.hotkey("tab")

# Copiando o assunto

pyperclip.copy(assunto)
pyautogui.hotkey("CTRL","v")
pyautogui.hotkey("tab")

#copiando a mensagem

pyperclip.copy(mensagem)
pyautogui.hotkey("CTRL" ,"v")

#Enviando mensagem

pyautogui.click(2138,762)






time.sleep(5)
pyautogui.position()


# CÓDIGO COMPLETO

import yfinance
import pyautogui
import pyperclip
import webbrowser
import time 

ticker = input("Digite o código da ação desejada: ")



dados= yfinance.Ticker(ticker).history(start= "2020-01-01", end= "2020-12-31")
fechamento = dados.Close

maxima = round(fechamento.max(),2)
minima = round(fechamento.min(),2)
valor_medio = round(fechamento.mean(),2)



print(maxima)
print(minima)
print(valor_medio)

destinatario = "lucassaguilar500@gmail.com"
assunto = "Analises do projeto 02"

mensagem = f""""

Prezado gestor,


Seguem as analises solicitadas da ação {ticker}:

Cotação máxima: R$ {maxima}
Cotação minima: R$ {minima}
Valor médio:    R$ {valor_medio}



Qualquer duvida estou á disposição!


Atte.

"""


webbrowser.open("www.gmail.com")
time.sleep(3)


pyautogui.PAUSE = 3

pyautogui.click(2089,198)



pyperclip.copy(destinatario)
pyautogui.hotkey("CTRL","v")
pyautogui.hotkey("tab")

pyperclip.copy(assunto)
pyautogui.hotkey("CTRL","v")
pyautogui.hotkey("tab")



pyperclip.copy(mensagem)
pyautogui.hotkey("CTRL" ,"v")



pyautogui.click(2138,762)


pyautogui.hotkey("CTRL", "F4")

print("E-mail enviado com sucesso")
