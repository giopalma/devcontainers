FROM haskell:9.14.1

# Installa dipendenze di sistema
# Crea utente non-root
RUN apt-get update && apt-get install -y \
    make \
    curl \
    git \
    procps \
    && rm -rf /var/lib/apt/lists/* \ 
    && apt-get clean \
    && useradd -ms /bin/bash vscode 

USER vscode
WORKDIR /home/vscode

# Aggiorna cabal e installa i tool nell'ambiente utente
RUN cabal update && cabal install happy alex BNFC

# Aggiunge i binari cabal al PATH
ENV PATH="/home/vscode/.cabal/bin:${PATH}"

WORKDIR /workspaces