.. image:: https://travis-ci.com/EuMari/se_hello_printer_app.svg?branch=master
    :target: https://travis-ci.com/EuMari/se_hello_printer_app

.. image:: https://app.statuscake.com/button/index.php?Track=2bott0wSjh&Days=1&Design=1
    :target: https://www.statuscake.com

Simple Flask App
================

Aplikacja Dydaktyczna wyświetlająca imię i wiadomość w różnych formatach dla zajęć
o Continuous Integration, Continuous Delivery i Continuous Deployment.


- Jeżeli nie istnieje, tworzymy plik Makefile, zawierający następujące komendy:

.PHONY: test


deps:
			pip install -r requirements.txt; \
			pip install -r test_requirements.txt

test:
			PYTHONPATH=. py.test
			PYTHONPATH=. py.test  --verbose -s

lint:
			flake8 hello_world test

run:
			PYTHONPATH=. FLASK_APP=hello_world flask run


- Rozpocząnając pracę z projektem (wykorzystując virtualenv). Hermetyczne środowisko dla pojedyńczej aplikacji w python-ie:

  ::

    # ubuntu, add to ~/.bashrc
    $ source /usr/local/bin/virtualenvwrapper.sh

    # tworzymy hermetyczne środowisko dla bibliotek aplikacji:
    $ mkvirtualenv wsb-simple-flask-app
    $ pip install -r requirements.txt
    $ pip install -r test_requirements.txt

    # albo:
    $ mkvirtualenv wsb-simple-flask-app
    $ make deps

    # jeżeli środowisko korzysta z innego interpretera, niż potrzebny do uruchomienia aplikacji:
    $ source /usr/local/bin/virtualenvwrapper.sh
    $ mkvirtualenv -p /usr/bin/python wsb-simple-flask-app  # mkvirtualenv -p {ścieżka do potrzebnego interpretera} wsb-simple-flask-app

  Sprawdź: `documentację virtualenvwrappera <https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html>`_ oraz `biblioteki flask <http://flask.pocoo.org>`_.




- Uruchamianie applikacji:

  ::

    # jako zwykły program
    $ python main.py

    # albo:
    $ PYTHONPATH=. FLASK_APP=hello_world flask run

    # albo z wykorzystaniem Makefile:
    $ make run

- Uruchamianie testów (see: http://doc.pytest.org/en/latest/capture.html):

  ::

    $ PYTHONPATH=. py.test
    $ PYTHONPATH=. py.test  --verbose -s

    # albo z Makefile:
    $ make test

- Kontynuując pracę z projektem, aktywowanie hermetycznego środowiska dla aplikacji py:

  ::

    $ source /usr/local/bin/virtualenvwrapper.sh # nie trzeba, jeśli już w .bashrc
    $ workon wsb-simple-flask-app

    ...

    # deaktywacja virtualenv
    $ deactivate

- Integracja z TravisCI:

  ::

    ...
- Monitoring aplikacji
    # statuscake test: hello_app
    # group alert: hello_world

Pomocnicze
==========

Ubuntu
------

- Instalacja python virtualenv i virtualenvwrapper:

  ::

    $ sudo pip install virtualenv
    $ sudo pip install virtualenvwrapper

- Instalacja dockera: `dockerce howto <https://docs.docker.com/install/linux/docker-ce/ubuntu/>`_


  ::

    $ yum remove docker \
        docker-common \
        container-selinux \
        docker-selinux \
        docker-engine

    $ yum install -y yum-utils

    $ yum-config-manager \
      --add-repo \
      https://download.docker.com/linux/centos/docker-ce.repo

    $ yum makecache fast
    $ yum install -y docker-ce
    $ systemctl start docker

Materiały
=========

- https://virtualenvwrapper.readthedocs.io/en/latest/
