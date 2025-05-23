#Criando imagem
FROM ubuntu:latest

#Comandos iniciais para instalação do dns
RUN apt update -y 
RUN apt install bind9 dnsutils -y

COPY named.conf.local /etc/bind

COPY db.asa.br /etc/bind

# Todo container docker precisa de um ponto de entrada/execução para 
# manter o container em funcionamento
# ENTRYPOINT [ "executable" ]
# No caso abaixo, o serviço chamado named (bind) é executado em primeiro plano
EXPOSE 53/tcp
EXPOSE 53/udp

CMD ["/usr/sbin/named", "-g", "-c", "/etc/bind/named.conf", "-u", "bind"]