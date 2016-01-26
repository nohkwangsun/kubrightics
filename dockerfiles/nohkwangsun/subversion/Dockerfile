FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install -y curl net-tools subversion

EXPOSE 3690

CMD mkdir -p /svn/log && \
    svnadmin create --fs-type fsfs /svn && \
    echo “anon-access = read” >> /svn/conf/svnserve.conf && \
    echo “auth-access = write” >> /svn/conf/svnserve.conf && \
    echo “password-db = passwd” >> /svn/conf/svnserve.conf && \
    echo “brightics = brightics” >> /svn/conf/passwd && \
    svnserve -d --listen-port 3690 --log-file /svn/log/svn.log -r /svn && \
    tail -100f /svn/log/*
