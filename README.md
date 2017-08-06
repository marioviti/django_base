# django_base
Ambiente di sviluppo base per Django:
un'applicazione minima per poter poi sviluppare siti web più complessi.

Cosa comprende:
* configurazione per deploy su Heroku.
* app_base con un esempio di blog e form per l'inserimento.
* bootstrap CDN.

## Installazione

* Dalla cartella nella quale installare il progetto
  * `$ python3 -m venv virtual_env`
  * `$ source /bin/activate`
  * `(virtual_env)$`


* Clonare la repo
  * `(virtual_env)$ git clone https://github.com/marioviti/django_base.git`


* Installare le dipendenze
  * `(virtual_env)$ pip install -r requirements.txt`


* Test di funzionamento
  * `(virtual_env)$ gunicorn django_base.wsgi --log-file -`

## Deploying su heroku

* createvi un profilo su heroku gratuitamente:
[heroku]( https://www.heroku.com/)


* da terminale eseguire il login:
  * `$ heroku login`


* posizionatevi nella root della repo e create un'app
  * `$ heroku create <nome_app>`


* far puntare dalla repo l'app di heroku
  * `$ heroku git:remote --app <nome_app>`


* disattivare collectstatic (in migration è la migliore opzione)
  * `heroku config:set DISABLE_COLLECTSTATIC=1`


* push sul server di heroku per effettuare il deploy
  * `$ git push heroku master`


* (opzionale)  nel caso ci fossero errori visualizzare il log con `$ heroku log`


* Sincronizzare il databases
   * `$ heroku run bash`
   * `$ python manage.py makemigrations`
   * `$ python manage.py migrate`

* Crea un super user
  * `python manage.py createsuperuser`

* visualizzare l'applicazione da browser
  * `$ heroku open`

* accedere al pannello admin:
  * aggiungere `/admin` alla fine del nome del dominio nella barra del browser
  * mettere le credenziali appena create
