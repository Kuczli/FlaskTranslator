# WSB Projek zaliczeniowy - FlaskTranslator

Projekt stworzony na potrzeby zaliczenia przedmiotu: 
Usługi i platformy deweloperskie dla aplikacji w Chmurze

Repozytorium:  https://github.com/Kuczli/FlaskTranslator
Link: https://flasktranslatorone.azurewebsites.net/ (może już nie działać)

Aplikacja **FlaskTranslator**
![podgląd działania](https://i.imgur.com/uTXcEmt.gif) 

# Zawartość
* [Technologie](#Technologie)
* [Deployment](#Deployment)
* [Komendy do utworzenia projektu z github'a](#Komendy)

## Technologie
Python 3.9.2
Flask    2.0.2
Jinja2   3.0.3
Bootstrap 4.5.3
i inne...

## Deployment
Aplikacja jest hostowana w [Azure](https://portal.azure.com/)
Wykorzystane zasoby chmury:

 - [App Service](https://docs.microsoft.com/pl-pl/azure/app-service/)
 - [Translator](https://docs.microsoft.com/pl-pl/azure/cognitive-services/translator/) 
 

## Komendy

#BASH - Pobranie repozytorium na pulpit
   

    git clone https://github.com/Kuczli/FlaskTranslator
#BASH - Utworzenie środowiska lokalnego > aktywacja (w folderze FlaskTranslator)

    py -3 -m venv .venv
    source .venv\\scripts\\activate

Korzystam z [PyCharm Community Edition](https://www.jetbrains.com/pycharm/)
Wczytanie bibliotek

    pip install -r requirements.txt

Tworzenie środowiska chmurowego przez [Azure CLI](https://docs.microsoft.com/pl-pl/cli/azure/)

Logowanie

    az login
Tworzenie grupy zasobów

    az group create -n FlaskTranslator -l westeurope
Tworzenie plan App Service

    az appservice plan create --name FlaskTranslator --resource-group FlaskTranslator --sku B1 --is-linux
  Tworzenie nową App Service internetową
  

    az webapp create --name FlaskTranslatorOne --runtime 'PYTHON|3.9' --plan FlaskTranslator --resource-group FlaskTranslator --query 'defaultHostName' --output table

Pełny poradnik wgrania Repo do App Service: [LINK](https://docs.microsoft.com/pl-pl/azure/app-service/quickstart-python?tabs=flask,windows,azure-cli,terminal-bash,local-git-deploy,deploy-instructions-azportal,deploy-instructions-zip-azcli)

