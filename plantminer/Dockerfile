FROM rocker/shiny-verse:latest

RUN mkdir /root/app/
COPY app.R /root/app/
RUN apt-get update && apt-get install -y git-all \
  && rm -rf /var/lib/apt/lists/*
RUN R -e 'install.packages(c("shiny", "shinydashboard", "DT", "devtools", "stringdist"))'
RUN git clone https://github.com/gustavobio/tpldata.git
RUN git clone https://github.com/gustavobio/tpl.git
RUN git clone https://github.com/gustavobio/flora.git
RUN R -e 'devtools::install("tpldata")'
RUN R -e 'devtools::install("tpl")'
RUN R -e 'devtools::install("flora")'

EXPOSE 3838
CMD ["R", "-e", "shiny::runApp('/root/app/', host = '0.0.0.0', port = 3838)"]
