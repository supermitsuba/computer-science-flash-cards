FROM ubuntu:latest
MAINTAINER Jorden Lowe "jordenashleylowe@gmail.com"
RUN apt-get update -y && \
    apt-get install -y python3-pip python3-dev build-essential git
RUN pip3 install virtualenv
RUN mkdir /var/www
WORKDIR /var/www
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
RUN virtualenv myprojectenv
RUN source myprojectenv/bin/activate
RUN git clone https://github.com/supermitsuba/computer-science-flash-cards.git /var/www/cs_flash_cards
WORKDIR /var/www/cs_flash_cards
RUN pip3 install uwsgi flask

EXPOSE 5000

CMD uwsgi --socket 0.0.0.0:5000 --protocol=http -w wsgi:app
