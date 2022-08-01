FROM rocker/shiny-verse:latest

COPY app.R /srv/shiny-server/
RUN mkdir /root/app/
COPY app.R /root/app/
COPY flora_0.3.7.tar.gz .

RUN R -e 'install.packages(c("shiny", "shinydashboard", "DT", "devtools", "stringdist"))'
RUN R -e 'devtools::install_github("gustavobio/tpldata")'
RUN R -e 'devtools::install_github("gustavobio/tpl")'
RUN R -e 'devtools::install_github("gustavobio/flora")'

EXPOSE 3838
CMD ["R", "-e", "shiny::runApp('/root/app/', host = '0.0.0.0', port = 3838)"]
